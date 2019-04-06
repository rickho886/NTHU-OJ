#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int grammar[100][100];
int grammar_size[100];
int sentence[100];
int N, M;
int pos, length;

bool solve(int rightBound)
{
    int i, j;
    int s_pos = pos;

    for(i = 0; i < N; i++)
    {
        pos = s_pos;
        for(j = 0; grammar[i][j] != -1 && pos <= rightBound; j++)
        {
            // construct another spell
            if(grammar[i][j] == 0)
            {
                if(!solve(rightBound - (grammar_size[i] - (j+1))))
                    break;
            }
            // not match -> turn to test next grammar
            else if(sentence[pos] != grammar[i][j])
                break;
            // if match, increase position index by 1
            else
                pos++;
        }

        // if whole grammar match spell, return true
        if(grammar[i][j] == -1 && pos == rightBound+1)
            return true;
    }
    return false;
}

int main() {
	scanf("%d%d", &N, &M);

	for (int i = 0; i < N; i++) {
		int x = 0, tmp;
		while (scanf("%d", &tmp) && tmp != -1)
			grammar[i][x++] = tmp;
		if (grammar[i][0] == 0 && x == 1)
        {
            N--;
            i--;
            continue;
        }
		grammar[i][x] = -1;
		grammar_size[i] = x;
	}
	for (int i = 0; i < M; i++) {
		int x = 0, tmp;
		while (scanf("%d", &tmp) && tmp != -1)
			sentence[x++] = tmp;
		sentence[x] = -1;
		length = x;
		pos = 0;
		if (solve(length-1))
            printf("True\n");
		else
            printf("False\n");
	}
	return 0;
}

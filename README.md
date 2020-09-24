#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int RockPaperScissor(char you, char computer)
{
    // returns 1 if you win, -1 if you lose and 0 if it is a draw
    // Condition for draw
    // Cases covered:
    // rock-rock
    // paper-paper
    // scissor-scissor
    if (you == computer)
    {
        return 0;
    }

    // Non-draw conditions
    // Cases covered:
    // rock-paper
    // paper-rock
    // rock-scissor
    // scissor-rock
    // paper-scissor
    // scissor-paper

    if (you == 'r' && computer == 'p')
    {
        return -1;
    }
    else if (you == 'p' && computer == 'r')
    {
        return 1;
    }

    if (you == 'r' && computer == 's')
    {
        return 1;
    }
    else if (you == 's' && computer == 'r')
    {
        return -1;
    }

    if (you == 'p' && computer == 's')
    {
        return -1;
    }
    else if (you == 's' && computer == 'p')
    {
        return 1;
    }
}
int main()
{
    int i = 1, your_count = 0, comp_count = 0;
    char you, computer;

    printf("--------------------\t\t\t\t\t\tRock Papers Scissors\t\t\t\t\t\t--------------------\n\n");
    printf("--------------------\t\t\t\t\t\t(First to 5)\t\t\t\t\t\t--------------------\n\n\n\n");

    while (i != 0)
    {
        //taking user's choice
        printf("\n\nRock(r),  Paper(p)  or  Scissors(s)?   ");
        scanf("%c", &you);
        fflush(stdin);

        srand(time(0)); //generating a random choice from computer
        int number = rand() % 100 + 1;

        if (number < 33)
        {
            computer = 'r';
        }
        else if (number >= 33 && number < 66)
        {
            computer = 'p';
        }
        else
        {
            computer = 's';
        }

        //Calling the game function to decide winner
        int result = RockPaperScissor(you, computer);

        //Showing the decisions
        printf("\nYou chose %c and Computer chose %c. ", you, computer);

        //Winner showcase
        if (result == 0)
        {
            printf("\n\nThe round Tied.");
        }
        else if (result == 1)
        {
            your_count++;
            printf("\nYou won %d times.", your_count);
        }
        else if (result == -1)
        {
            comp_count++;
            printf("\nComputer won %d times.", comp_count);
        }
        if (your_count == 5 || comp_count == 5)
        {
            i = 0;
        }
        else
        {
            i = 1;
        }
    }
    if (your_count > comp_count)
    {
        printf("\n\nYou won the game!!");
    }
    else
    {
        printf("\n\nComputer won the game!!");
    }
    return 0;
}

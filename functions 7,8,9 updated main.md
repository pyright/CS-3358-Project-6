/*
 Author: Michael Campos (#5) and Justin Couture (#10)
 Due Date: 4 November 2015
 Programming Assignment Number 6
 Fall 2015 - CS 3358 - Section 3

 Instructor: Husain Gholoom

 The purpose of this program is........

 to perform recursive operation on an array
 */

#include <iostream>
#include <time.h>
#include <cstdlib>

using namespace std;

//******************************************************************************
//PROTOTYPES
int getArraySize();                     // Gets user input for array size
void fillArray(int[], int);// Fills array with random values between 1 and 100
void showArrayContent(int [], int);     // Show the contents of the array
void isItPrime(int [], int, int);       // Output all the primes.
int sumOfSquares(int [], int, int, int);// find the sum of squares return
int minNumber(int [], int);             // find the minimum number and return
int maxNumber(int [], int);             // find the maximum number and return
//******************************************************************************


//******************************************************************************
//MAIN
int main()
{
    int a =0;  // variable for recursive traversal
    int number = 0; //variable for returned integers

    //Set array size
    int theArraySize = getArraySize();

    //Create array
    int theArray[theArraySize]; //Declare array

    //Fill array
    fillArray(theArray, theArraySize);

    //Show array content
    cout<<"The generated array is: ";
    showArrayContent(theArray, theArraySize);
    cout<<"\n";

    //Returns the min number
    number = minNumber(theArray, theArraySize);
    cout<<"\n\nThe minimum number in ";
    showArrayContent(theArray, theArraySize);
    cout<<"is: "<<number;
    number = 0;


    //Return the max number
    number = maxNumber(theArray, theArraySize);
    cout<<"\nThe maximum number in ";
    showArrayContent(theArray, theArraySize);
    cout<<"is: "<<number;
    number = 0;
    cout<<"\n";

    //Returns the Sum of Squares
    number = sumOfSquares(theArray, theArraySize, a, number);
    cout<<"\n\nThe Sum of squares between 0 and ";
    cout<<theArray[(theArraySize-2)]<<" is: "<<number<<endl;
    cout<<"\n";


    //Shows the prime numbers
    isItPrime(theArray, theArraySize, a);


    return 0;
}
//******************************************************************************


//******************************************************************************
//FUNCTIONS

//******************************************************************************
//  Get user input for array size
//******************************************************************************

int getArraySize()
{

    int arraySize; //Hold array size variable

    cout << "What size is your array?\n\nArray Size: "; //Prompt user for input
    cin >> arraySize; //Take input
    cout << endl; //Formatting

    return arraySize; //Return array size
}


//******************************************************************************
//  Fill the array with random integers between 1 and 100.
//******************************************************************************
void fillArray(int myArray[], int myArraySize)
{

    for ( int i = 0; i < myArraySize; i++)  //Traverse array
    {

        myArray[i] = ((rand() % 100) + 1); //Store random int
    }

    return;
}


//******************************************************************************
//  Display the content of the array
//******************************************************************************
void showArrayContent(int myArray[], int myArraySize)
{
    for(int j = 0; j < myArraySize; j++)
    {
        cout << myArray[j] << " ";
    }

    return;
}


//******************************************************************************
//  Return the minimum number of the array
//******************************************************************************
int minNumber(int myArray[], int length)
{
    if (length == 1)
    {
        return myArray[0];
    }
    int minimum = minNumber((myArray+1), (length-1));


    if (minimum > myArray[0])
    {
        minimum = myArray[0];
    }

    return minimum;
}


//******************************************************************************
//  Return the maximum number of the array
//******************************************************************************
int maxNumber(int myArray[], int length)
{
    if (length == 1)
    {
        return myArray[0];
    }
    int maximum = maxNumber((myArray+1), (length-1));


    if (maximum < myArray[0])
    {
        maximum = myArray[0];
    }

    return maximum;
}




//******************************************************************************
//  Return the sum of Squares from 0-(size -2)
//******************************************************************************
int sumOfSquares(int myArray[], int length, int a, int sum)
{
    if (a == myArray[(length-2)])
    {
        sum = (a*a);
        return sum;
    }

    sum = sumOfSquares(myArray, length, (a+1), sum);

    sum = (a*a) + sum;

    return sum;
}


//******************************************************************************
//  Display the primes
//******************************************************************************
void isItPrime(int myArray[],int length, int a)
{
    int i = 0; //variable for switch statement

    if (a == (length))   // what to do on the last element before going back
    {
        cout << "\nisItPrime:  \n\n";
        return;
    }


    isItPrime(myArray, length, (a+1));

    i = myArray[a];
        switch(i)
        {
        case 2: cout<<"The number 2 IS prime\n"; break;
        case 3: cout<<"The number 3 IS prime\n"; break;
        case 5: cout<<"The number 5 IS prime\n"; break;
        case 7: cout<<"The number 7 IS prime\n"; break;
        case 11: cout<<"The number 11 IS prime\n"; break;
        case 13: cout<<"The number 13 IS prime\n"; break;
        case 17: cout<<"The number 17 IS prime\n"; break;
        case 19: cout<<"The number 19 IS prime\n"; break;
        case 23: cout<<"The number 23 IS prime\n"; break;
        case 29: cout<<"The number 29 IS prime\n"; break;
        case 31: cout<<"The number 31 IS prime\n"; break;
        case 37: cout<<"The number 37 IS prime\n"; break;
        case 41: cout<<"The number 41 IS prime\n"; break;
        case 43: cout<<"The number 43 IS prime\n"; break;
        case 47: cout<<"The number 47 IS prime\n"; break;
        case 53: cout<<"The number 53 IS prime\n"; break;
        case 59: cout<<"The number 59 IS prime\n"; break;
        case 61: cout<<"The number 61 IS prime\n"; break;
        case 67: cout<<"The number 67 IS prime\n"; break;
        case 71: cout<<"The number 71 IS prime\n"; break;
        case 73: cout<<"The number 73 IS prime\n"; break;
        case 79: cout<<"The number 79 IS prime\n"; break;
        case 83: cout<<"The number 83 IS prime\n"; break;
        case 89: cout<<"The number 89 IS prime\n"; break;
        case 97: cout<<"The number 97 IS prime\n"; break;
        default: cout<<"The number: "<<myArray[a]<<" is NOT prime\n";
        }
        return;
}


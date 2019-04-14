#include<iostream.h>
#include<conio.h>
#include<stdlib.h>
#include<stdio.h>
#include<ctype.h>
struct hotel
{
 char cnm[50];  //customer name
 int ctype;     //type of room
 char cadd[70]; //customer adress
 long cno;      //customer mobile no.
 int nr;        //no. of rooms
 int nd;        //no. of days
 int cd;        //day of checkin
 int cmonth;    //month of checkin
 int cy;        //year of checkin
 int rno[100];   //room no.
 int fa;        //to store amt. of food
}h;
void edit_rec();  //for editing rec

void calc();      //for calculating bill

void change();    //for changing room

void main_menu();

void checkout();   //for finding out the checkout date

void food();       //for ordering food

void exit()
{
 int ch;   //to store choice
 cout<<endl<<endl<<"\t\t\t Enter 1 To Return To Previous Menu ";
 cout<<"\n\t\t\t Enter 2 To Exit ";
 cin>>ch;
 switch(ch)
 {
  case 1:main_menu();
	 break;

  case 2:exit(0);

  default:exit(0);
 }
}

void input()
{
 cout<<endl<<endl<<endl;
 cout<<"\t\t\t Enter Name:";
 gets(h.cnm);
 cout<<"\t\t\t Enter Address:";
 gets(h.cadd);
 cout<<"\t\t\t Enter Mobile No.:";
 cin>>h.cno;
 cout<<"\t\t\t Enter no. of room:";
 cin>>h.nr;
 cout<<"\t\t\t Enter no. of days:";
 cin>>h.nd;
 cout<<"\t\t\t Enter Date Of Checkin:";
 cin>>h.cd;
 cout<<"\t\t\t Enter Month Of Checkin:";
 cin>>h.cmonth;
 cout<<"\t\t\t Enter Year Of Checkin:";
 cin>>h.cy;
 for(int i=0;i<h.nr;i++)
 {
  cout<<"\t\t\t Enter Desired Room No.:";
  cin>>h.rno[i];
 }
 cout<<endl<<endl;
 cout<<"\t\t\t Details Stored !!!!"<<endl;
 cout<<endl<<endl;
 cout<<"\t\t\t 1 : Platinum Rooms - Rs 5000/day"<<endl;
 cout<<"\t\t\t 2 : Golden Rooms - Rs 4500/day"<<endl;
 cout<<"\t\t\t 3 : Silver Rooms - Rs 4000/day"<<endl;
 cout<<"\t\t\t Enter Choice:";
 cin>>h.ctype;
 cout<<"\t\t\t\t\t Press any key to continue";
 getch();
}
void print()
{
 float r;    //room no. alloted
 clrscr();
 cout<<endl<<endl<<endl;
 cout<<endl<<"\n\t\t\t CUSTOMER DETAILS";
 cout<<endl<<"\t\t\t Name : ";
 puts(h.cnm);
 cout<<endl<<"\t\t\t Address : ";
 puts(h.cadd);
 cout<<endl<<"\t\t\t Mobile No. : "<<h.cno;
 cout<<endl<<"\t\t\t No Of Rooms Required : "<<h.nr;
 cout<<endl<<"\t\t\t Room(s) Alloted : ";
 cout<<endl<<"\t\t\t No. Of Days : "<<h.nd;
 for(int j=0;j<h.nr;j++)
 {
  cout<<endl<<"\t\t\t "<<j+1<<" : Room No Is : "<<h.rno[j];
 }
 cout<<endl<<endl;
 exit();

}
void main()
{
 clrscr();
 cout<<endl<<"\t\t\t******************************";
 cout<<endl<<"\t\t\t   HOTEL MANAGEMENT PROJECT   ";
 cout<<endl<<"\t\t\t******************************";
 input();
 if(h.ctype>3)
 {
  clrscr();
  cout<<endl<<"\t\t\t Invalid Choice";
  cout<<endl<<"\t\t\t Try Again";
  input();
 }
 main_menu();
 getch();
}
void main_menu()
{
 int ch;   //for accepting choice
 float a;    //for storing amt of food
 clrscr();
 cout<<endl<<endl<<endl;
 cout<<endl<<"\t\t\t**********************";
 cout<<endl<<"\t\t\t      MAIN MENU       ";
 cout<<endl<<"\t\t\t**********************";
 cout<<endl<<"\t\t\t 1 : Customer Record";
 cout<<endl<<"\t\t\t 2 : Bill";
 cout<<endl<<"\t\t\t 3 : Change Room";
 cout<<endl<<"\t\t\t 4 : Edit Record";
 cout<<endl<<"\t\t\t 5 : Checkout";
 cout<<endl<<"\t\t\t 6 : Food";
 cout<<endl<<"\t\t\t 7 : Exit";
 cout<<endl<<"\n\t\t\t\t  Enter Choice ";
 cin>>ch;
 switch(ch)
 {
  case 1:print();
	 break;

  case 2:calc();
	 break;

  case 3:change();
	 break;

  case 4:edit_rec();
	 break;

  case 5:checkout();
	 break;

  case 6:food();
	 break;

  case 7:exit(0);
	 break;

  default:cout<<"\t\t\t Invalid Choice!!!Try Again";
	  main_menu();
 }
 getch();
}

void calc()
{
 int bill;
 switch(h.ctype)
 {
  case 1:bill=h.nd*5000;
	 break;

  case 2:bill=h.nd*4500;
	 break;

  case 3:bill=h.nd*4000;
	 break;

  default:bill=0;
 }
 clrscr();
 int ch,a;
 cout<<endl<<endl<<endl;
 cout<<endl<<"\t\t\t ********** BILL **********";
 cout<<endl<<endl<<"\t\t\t Name : ";
 puts(h.cnm);
 cout<<endl<<"\t\t\t Address : ";
 puts(h.cadd);
 cout<<endl<<"\t\t\t Room Charges : "<<bill;
 cout<<endl<<"\t\t\t Food Charges : "<<h.fa<<endl;
 cout<<endl<<"\t\t\t Net Amount : ";
 cout<<bill+h.fa;
 cout<<endl<<endl;
 exit();
}
void change()
{
 int x,y,ch;    //room changing variable
 clrscr();
 cout<<endl<<endl<<endl<<endl<<"\t\t\t ***** ROOM CHANGING MENU *****";
 cout<<endl<<endl<<endl<<"\t\t\t Your Roon No(s). are : ";
 for(int i=0;i<h.nr;i++)
 {
  cout<<endl<<"\t\t\t "<<i+1<<" : "<<h.rno[i];
 }
 cout<<endl<<endl<<"\t\t\t Enter Choice Of Room You Want To Change ";
 cin>>ch;
 cout<<endl<<endl<<"\t\t\t Enter Desired Room Number";
 cin>>x;
 cout<<endl<<endl<<"\t\t\t Sorry !! Room already booked or in use";
 cout<<endl<<endl<<"\t\t\t Try Again";
 cout<<endl<<endl<<"\t\t\t Enter Desired Room No.";
 cin>>y;
 if(x!=y)
 {
  cout<<endl<<endl<<"\t\t\t Room Changing Successful";
  cout<<endl<<endl<<"\t\t\t Your Current Room No. is : "<<y;
  h.rno[ch-1]=y;
 }
 else
 {
  cout<<endl<<endl<<"\t\t\t Sorry!!Room Already In Use ";
  cout<<endl<<endl<<"\t\t\t Try Again ";
  cout<<endl<<endl<<"\t\t\t\t Press Any Key To Continue ";
  getch();
  change();
 }
 cout<<endl<<endl;
 exit();
}
void edit_rec()
{
 int ch;      //to store choice
 clrscr();
 cout<<endl<<endl<<endl;
 cout<<endl<<"\t\t\t ******** PROFILE EDITING MENU ********";
 cout<<endl<<"\t\t\t 1 : Edit Name ";
 cout<<endl<<"\t\t\t 2 : Edit Address ";
 cout<<endl<<"\t\t\t 3 : Edit Mobile No. ";
 cout<<endl<<"\t\t\t 4 : Edit Type Of Room Choosed ";
 cout<<endl<<"\t\t\t 5 : Edit No Of Days ";
 cout<<endl<<"\t\t\t 6 : Edit No Of Rooms ";
 cout<<endl<<"\t\t\t\t Enter Choice ";
 cin>>ch;
 cout<<endl;
 switch(ch)
 {
  case 1:cout<<endl<<"\t\t\t Enter Name : ";
	 gets(h.cnm);
	 break;

  case 2:cout<<endl<<"\t\t\t Enter Address : ";
	 gets(h.cadd);
	 break;

  case 3:cout<<endl<<"\t\t\t Enter Mobile No. : ";
	 cin>>h.cno;
	 break;

  case 4:cout<<endl<<"\t\t\t Enter Choice : ";
	 cout<<endl<<"\t\t\t 1 : Platinum Rooms - Rs5000/day ";
	 cout<<endl<<"\t\t\t 2 : Golden Rooms - Rs4500/day ";
	 cout<<endl<<"\t\t\t 3 : Silver Rooms - Rs4000/day ";
	 cout<<endl<<"\t\t\t\t Enter Choice ";
	 cin>>h.ctype;
	 break;

  case 5:cout<<endl<<"\t\t\t Enter No Of Days : ";
	 cin>>h.nd;
	 break;

  case 6:cout<<endl<<"\t\t\t Enter No Of Rooms : ";
	 cin>>h.nr;
	 break;

  default:cout<<endl<<"\n\n\t\t\t Invalid Choice!!!Try Again ";
	  edit_rec();

 }
 cout<<endl<<endl<<"\t\t\t Profile Edited Successfully ";
 cout<<endl<<endl;
 exit();
}

void checkout()
{
 clrscr();
 int m=h.cmonth;
 int d=0,y;
 y=h.cy;
 cout<<endl<<endl<<endl;
 if((h.cd+h.nd)>=30)
 {
  m++;
  d=(h.cd+h.nd)%30;
 }
 if(m>=12)
 {
  y++;

 }
 cout<<endl<<"\t\t\t ******** CHECKOUT MENU ******** ";
 cout<<endl<<"\t\t\t Your Checkout Date is : (YYYY/MM/DD)\t"<<d<<"."<<m<<"."<<h.cy;
 exit();
}

void food()
{
  clrscr();
  int ch,ch1,n,a,ch2;
  cout<<endl<<endl<<endl;
  cout<<endl<<"\t\t\t ******** FOOD MENU ********";
  cout<<endl<<"\t\t\t 1 : Italian";
  cout<<endl<<"\t\t\t 2 : Chinese";
  cout<<endl<<"\t\t\t 3 : Indian";
  cout<<endl<<"\t\t\t 4 : Continental";
  cout<<endl<<"\t\t\t\t Enter The Choice Of Cuisine ";
  cin>>ch;
  cout<<endl<<endl;
  switch(ch)
  {
   case 1 :cout<<endl<<"\t\t\t 1 : Pasta e Fagioli ";
	   cout<<endl<<"\t\t\t 2 : Tacco Indiana ";
	   cout<<endl<<"\t\t\t 3 : Veg Xtravaganza ";
	   cout<<endl<<"\t\t\t 4 : Neapolitan Pizza ";
	   cout<<endl<<"\t\t\t 5 : Butter Scotch Mus Cake (Des.) ";
	   cin>>ch1;
	   cout<<endl<<endl<<"\t\t\t Enter No. Of Plates : ";
	   cin>>n;
	   switch(ch1)
	   {
	    case 1:a=1300;
		   break;

	    case 2:a=800;
		   break;

	    case 3:a=960;
		   break;

	    case 4:a=790;
		   break;

	    case 5:a=820;
		   break;

	    default:cout<<endl<<"\t\t\t Invalid Choice!!Try Again";
		    food();
	   }
	   h.fa=a*n;
	   cout<<endl<<endl<<"\t\t\t Your Total Amt For Food Is "<<a*n;
	   break;

   case 2:cout<<endl<<"\t\t\t 1 : Schewan Rice";
	  cout<<endl<<"\t\t\t 2 : Hakka Noodles " ;
	  cout<<endl<<"\t\t\t 3 : Garlic Sesoned Manchurian with Gravy ";
	  cout<<endl<<"\t\t\t 4 : Buddha's Delight ";
	  cout<<endl<<"\t\t\t 5 : Baozi (Des.) ";
	  cin>>ch1;
	  cout<<endl<<endl<<"\t\t\t Enter No. Of Plates : ";
	  cin>>n;
	  switch(ch1)
	  {
	   case 1:a=867;
		  break;

	   case 2:a=937;
		  break;

	   case 3:a=1452;
		  break;

	   case 4:a=699;
		  break;

	   case 5:a=1402;
		  break;

	   default:cout<<endl<<endl<<"\t\t\t Invalid Choice!!Try Again";
		   food();
	  }
	  h.fa=a*n;
	  cout<<endl<<endl<<"\t\t\t Total Amt. Of Food Is "<<a*n;
	  break;

   case 3:cout<<endl<<"\t\t\t 1 : Chicken Tikka Masala";
	  cout<<endl<<"\t\t\t 2 : Chhole Bhature";
	  cout<<endl<<"\t\t\t 3 : Dal Makkhani";
	  cout<<endl<<"\t\t\t 4 : Palak Paneer";
	  cout<<endl<<"\t\t\t 5 : Chicken Biryani";
	  cout<<endl<<"\t\t\t 6 : Ras-malai (Des.)";
	  cin>>ch1;
	  cout<<endl<<endl<<"\t\t\t Enter No. Of Plates : ";
	  cin>>n;
	  switch(ch1)
	  {
	   case 1:a=1000;
		  break;

	   case 2:a=2000;
		  break;

	   case 3:a=945;
		  break;

	   case 4:a=900;
		  break;

	   case 5:a=1500;
		  break;

	   case 6:a=400;
		  break;

	   default:cout<<endl<<"\t\t\t Invalid choice!!try Again";
		   food();

	  }
	  h.fa=a*n;
	  cout<<endl<<endl<<"\t\t\t Total Amt Of Food Is "<<a*n;
	  break;

   case 4:cout<<endl<<"\t\t\t 1 : Del Frisco";
	  cout<<endl<<"\t\t\t 2 : Smooky Grilled Kabab";
	  cout<<endl<<"\t\t\t 3 : Le-Bon Cake";
	  cout<<endl<<"\t\t\t 4 : Sizzlers Pane Sciocco";
	  cout<<endl<<"\t\t\t 5 : Darclay Prime (Des.)";
	  cin>>ch1;
	  cout<<endl<<endl<<"\t\t\t Enter No. Of Plates : ";
	  cin>>n;
	  switch(ch1)
	  {
	   case 1:a=600;
		  break;

	   case 2:a=689;
		  break;

	   case 3:a=567;
		  break;

	   case 4:a=999;
		  break;

	   case 5:a=998;
		  break;

	   default:cout<<endl<<endl<<"\t\t\t Invalid Choice!!Try Again";
		   food();
	  }
	  h.fa=a*n;
	  cout<<endl<<endl<<"\t\t\t Total Amt. Of Food Is "<<a*n;
	  break;


   default:cout<<endl<<"\t\t\t Invalid Choice!!Try Again";
	   food();

  }
   exit();
 }






---
title: "regarding installing softwares,ide,compilers......"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by 12averma on 2010-07-10
hello every one........!!
i m currently using window vista..........nd also have installed ubuntu-10.04-desktop-i386
and it is running well.But i m facing problems in following things

1. that i dont know how to connect to internet (i m using bsnl ADSL 2+ Modem/Router which is connect through telephone line.).So please help me which package shuld i install(plz give exact address)....nd please give step by step solution for connection.

2.second problem is that i want to run my c program (which perfectly run on vista but not on ubuntu).so how can i install borland turbo c++ on ubuntu.......and please also help ..how to compile and execute c or c++ programs..........

3.third problem is related to installing jdk1.6.0 on ubuntu.please give exact address of corresponding package.......nd m in confusion ......after installing package shuld i install jdk1.6.0 or not..(because i searched some package ,installed it,then tried to install jdk1.6.0 but not got success.........so please help me.......

4.forth problem is related to installation of microsoft visual studio 2008......using .net3.5 framework...........please help me

I WOULD B HIGHLY.....HIGHLY THANKFUL TO ANYONE WHO HELP ME IN SOLVING ABOVE PROBLEMS.........

---

### Post by viralmeme on 2010-07-10
> **12averma said:**
> 1. that i dont know how to connect to internet (I'm using bsnl ADSL 2+ Modem/Router which is connect through telephone line.). So please help me which package shuld i install(plz give exact address)....nd please give step by step solution for connection.
01. A default Ubuntu 10.04 distro will pick up a connection to the Internet - by default, without requiring the installation any extra software. All is required is to plug the computer into the modem using a CAT5 cable and turn it on. Do you have a cable like the one depicted in the image below?

[IMG]http://www.ccpowerpc.com.au/zencart/images/cat5.jpg[/IMG]

---

### Post by 12averma on 2010-07-10
THANK YOU SIR FOR YOUR ANSWER....!..but Respected Sir, i am already using above type of cable but (modem adsl +2) connection get detected only on windows vista but not on ubuntu10.04. I even saw help given in ubuntu os but there they say to go to system->administrator->network. but when i try to go to this path network option does not occur there but i get other option instead of this which is network tool,So whole path that i obtain is system->administrator->network tool.so overall ,i am not able to connect to internet even using the type of cable as shown by you.

---

### Post by rogerdg on 2010-07-10
You might look for the network-manager icon at the top of your display (somewhere close to and to the left of your user name) Right clicking on it will open a list of options which include enable networking (for wired) and enable wireless (for wireless) and below those options an item "Edit Connections..." which you use to configure the network.  The icon for this looks like a series of semi-circles above a dot for wireless or a network cable end for wired networks.  In your case you need to configure a new wired network.

For your Turbo-C application try using wine (WINdos Emulator) or DOSBOX.  Wine allows you to use some windows applications under linux while DOSBOX allows you to use any DOS based application in linux.  I have not had much success with wine (it doesn't like most of my applications) but DOSBOX has correctly run every DOS program that I've used with it.

JDK and Microsoft .NET installations are outside my realm of experience so I can't be helpful there.

---

### Post by dineshs on 2010-07-11
In a terminal(application-accessories-terminal) type 
```
ifconfig -a
```and enter.Post back the results you get.
What is the model name of your modem?Is there an internet/data lamp
? If yes is it blinking?
How do you connect in windows?Do you have a pppoe dialler with your username , password and connect button?

---

### Post by viralmeme on 2010-07-12
> **12averma said:**
> i am already using above type of cable but (modem adsl +2) connection get detected only on windows vista but not on ubuntu10.04.

sOrry to hear that, well, you got me stumped there. Oh, btw, could you post your `c pRogrAm' so as we can help you getting that running, what's its nAME again ?

---

### Post by 12averma on 2010-07-12
> **viralmeme said:**
> sOrry to hear that, well, you got me stumped there. Oh, btw, could you post your `c pRogrAm' so as we can help you getting that running, what's its nAME again ?
sir i want to know which c compiler sud i use (nd how to install that compiler) in ubuntu10.04 so that any C or C++ program can be executed.....
a simple program can be as....

#include<stdio.h>
#include<conio.h>
void main()
{
clrscr();
printf("this is my first program execution on ubuntu10.04");
getch();
}

---

### Post by 12averma on 2010-07-12
> **dineshs said:**
> In a terminal(application-accessories-terminal) type 
```
ifconfig -a
```and enter.Post back the results you get.
What is the model name of your modem?Is there an internet/data lamp
? If yes is it blinking?
How do you connect in windows?Do you have a pppoe dialler with your username , password and connect button?
sir .....modem is basically of bsnl adsl ......connected through phone line.......working properly with all 4 leds working......... but problem is that it works on vista very well but connection do not get established on ubuntu........
when i run ubuntu......modem's all light glows vry well but ......connection doesnt get established........shud i use any package or any thingelse so that modem get detected nd even connected.........(i didnt use ny software to connect modem wid window vista......i jst opne vista->turn modem on->connectto->broadband connection->then i enter username nd password ->connect .......nd consequntly connection get established......)

---

### Post by dineshs on 2010-07-14
Sorry to say that your answer is not clear.```
ifconfig -a
```?
Anyway pl try this
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the DSL tab- click add - Enter username and password-tick available to all users-apply(connection name =DSL connection by def)

To connect DSL click on NM icon click `DSL connection'

---

### Post by 12averma on 2010-07-15
> **dineshs said:**
> sorry to say that your answer is not clear.```
ifconfig -a
```?
Anyway pl try this
right-click on the nm icon(two opposite arrows on top right) and then click on edit connections. 
Select the dsl tab- click add - enter username and password-tick available to all users-apply(connection name =dsl connection by def)

to connect dsl click on nm icon click `dsl connection'
thanku sir dineshs................:)...................finaly m connectd to internet.............nd dis msg is send using d net on ubuntu...................:)..................thnx alot..........!!!!!!!!!!!!!!:d

---

### Post by dineshs on 2010-07-15
Enjoy ubuntu and mark this thread as SOLVED via thread tools

---


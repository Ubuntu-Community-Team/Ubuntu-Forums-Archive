---
title: "Help installing &amp; running BF2142cc"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by fatray on 2007-05-29
I've been using ubunu on and off for a little while now.  Getting the hang of it very little, but this program eludes me completely.  It's a Windows program, it comes with instructions on how to run with Linux but I just can't get it to run to save my life.  First I tried right clicking "RUN WITH WINE".  This does nothing and acts like I tapped on my monitor with my finger, nothing LOL.  The directions says it works with Mono, I think I installed it. 
I guess one of my main problems is the file system.  I don't know how to type in the commands in Terminal to find the folder where 2142cc is.  I know this sounds crazy but for some reason C:\BF2cc\BF2cc.exe" doesn't work.   So I keep trying the right click "run with" option that never works.
[http://infinity-gamehosting.net/howto/Battlefield2142_and_2142CC_on_Linux/index-05.html](http://infinity-gamehosting.net/howto/Battlefield2142_and_2142CC_on_Linux/index-05.html)

All I want to run is the 2142cc Damon on my UNBUNU PC to control my BF2142 server in St. Louis while I play the game on my windows machine.

Following the direction from link above this is where my troubles start below.
fatray@FATRAY-Upstairs-Linux:~$ mono bf2ccd.exe
Cannot open assembly bf2ccd.exe.

What am I doing wrong??  The BF2142cc folder is on my desktop with bf2cc.exe inside.

---

### Post by Choc_Salties on 2007-11-10
BF2CCD needs to sit directly on top of your BF2 SERVER installation, as it controls the actual server daemon itself - you would have to install that on your actual server. 

What i think you are trying to do is use the BF2CC client which is a different kettle of fish. The client component is meant for controlling your server, which yes, does also run under Linux (Ubuntu); although in both cases mono is required.

However if your are using Windows to play BF2, then i'd suggest also using the client under Windows as well. I do.

The BF2CC.com site does also include a walkthrough for BF2CC server and client installation for both Windows and Linux. 

To install mono, just open up a terminal window (or switch to a console) and at the prompt type "sudo apt-get install mono" (without the quotes), type in your password ; "yes" to download and install...

---


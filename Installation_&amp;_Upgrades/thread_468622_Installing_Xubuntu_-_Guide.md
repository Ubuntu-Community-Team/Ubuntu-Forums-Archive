---
title: "Installing Xubuntu - Guide"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by GuiderGuy on 2007-06-09
I have heared that you want to install Xubuntu on your computer , and I tell you now - you have made a good choice . 

You now browse to ShipIt , and search for the Xubuntu CD . You suddendly get surprised by the fact that Xubuntu has no support from ShipIt . You feel frustrated . You want Xubuntu so badly , but you can't really get it from ShipIt (or Downloading it ..) . You could have never felt more frustrated .

If this is the case , than this guide if for you . Start by going into ShipIt , and order your favourite distro (Ubuntu / Kubuntu or Edubuntu) . Three weeks later , the CD's arrive . You open the case , pop your distro into your CD-Rom , and install it . But then you wonder 'This is not what I have wanted from the first place!' and again , frustration takes place .

My guide , will walk you through this situation , and if you followed it correctly , You will have Xubuntu installed by the end of this guide .

So , let's start from the point of which you installed a fresh , clean copy of Ubuntu/Kubuntu or Edubuntu .
Open up the terminal , and type the following command ;

[FONT="Courier New"][COLOR="Teal"]sudo aptitude update && sudo aptitude install xubuntu-desktop[/COLOR][/FONT]

You will most lilkely will be asked for your password , type it in (It's the same password that you have set while installing your distro) .

Now , you must wait while the Aptitude is downloading Xubuntu desktop (and packages) to your computer , it will take approximately one hour if your sitting on a 1.5 kbps connection .

At some point , aptitude will ask your about your 'Display Manager' , the display manager is the program that provides a log-in box when you boot your PC . KDE has its own display manager (called kdm) that replaces Gnome's (called gdm). You'll be asked which display manager should be enabled. The choice is yours (use the arrow and Enter keys to respond to the text-based dialog box).

After setting up the 'Display Manager' , you will have 10 more minutes which will be dedicated to installing everthing that you have downloaded . When it all ends (You will be prompted with a new command line) , restart your PC . You should now see the Xubuntu Login screen - Good job , you've completed 75% of your Xubuntu installation .

Wait , when you start up the tools panel , you can see all the tools that were inside your previous distro (Kubuntu tools , Ubuntu tools ..) . You can now choose if you WANT to delete those tools , or if you DONT WANT them to be deleted .

Type the following commands (to delete Ubuntu or Kubuntu desktops , forever !)

[COLOR="Teal"][FONT="Courier New"]sudo aptitude remove kubuntu-desktop[/FONT][/COLOR]

OR

[COLOR="teal"][FONT="Courier New"]sudo aptitude remove ubuntu-desktop[/FONT][/COLOR]

This is not all , you now must delete all the tools . To delete the tools if you are running a Xubunti Fiesty Fawn , visit [here]("http://www.psychocats.net/ubuntu/purexfce") . If your using Edgy , go [here]("http://www.psychocats.net/ubuntu/purexfceedgy"). If your on a Dapper , go [here]("http://www.psychocats.net/ubuntu/purexfcedapper").

> **Choosing boot graphics:** To select artwork for the boot and shutdown screens, enter the following two commands in a Terminal window:
[COLOR="Teal"]
**sudo update-alternatives --config usplash-artwork.so**[/COLOR]

[COLOR="Teal"]**sudo update-initramfs -u**[/COLOR]

After you enter the first command, you'll be given a choice among Ubuntu, Kubuntu, or Xubuntu-themed artwork (assuming you've installed these desktop meta-packages). Type the number that corresponds to your choice and press Enter. Then issue the second command (which will take a few moments to run; have patience).

Congratulations , you are now an officiall XUBUNTU USER ! - Good job for completing this guide :popcorn: !

--------------------------------------------------------------------------------------------------------------------------------

Information taken from -
*1) [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)
*2) [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
*3) [http://www.ecoustics.com/pcw/howto/132030](http://www.ecoustics.com/pcw/howto/132030)


[RIGHT]Written (and rewritten ..) by GuiderGuy[/RIGHT]

---

### Post by Mets on 2007-06-10
awesome, finally pure Xfce!!  Thanks a bunch!

---

### Post by GuiderGuy on 2007-06-11
> awesome, finally pure Xfce!! Thanks a bunch!

I am really glad I could help you ! :p !

---

### Post by eeried on 2007-06-27
Nice guide, congrats. Thouh how you install ubuntu from a shipit CD on a computer which requires Xubuntu rather than Ubuntu is beyond me! As I see it, you can't install Ubuntu on an old computer from the LIve6CD, you need the alternate CD.

Then if you're short of space on your HDD you ought to remove ubuntu-desktop before installing xubuntu-desktop, I should think.

Many thanks for mentioning removing the tools!

---

### Post by GuiderGuy on 2007-07-07
I've wrote this following my harsh experiment with not being able to install both LiveCD and Alternative .
Removal of Ubuntu-Desktop is mentioned in the guide :)

---


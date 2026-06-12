---
title: "Help installing ubuntu!!"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by ferjonathas on 2010-04-28
How do you actually install ubuntu??  I cant figure it out, its nothing like windows!!  I download the unetbootin to make a boot usb drive.. I did that but when it boots it ask goes blue with a thing flash default.. Then it asks me to press tab, when i do that it comes with a cmd.. what should a write??  if i click esc on the keyboard it brings a cmd line.  if i write like E:\dir it says kernel invalid.

what is a cmd that runs the cd on a boot for ubuntu

how hard is to install it??

---

### Post by carl4926 on 2010-04-28
Is using a CD not an option for you?

It doesn't sound like your usb device is working properly.

---

### Post by ferjonathas on 2010-04-28
Have you used UNEbootin??

Well it goes like this..

it asks for distribution

Ubuntu CD live 9.10

then goes to diskimage 

I choose ISO then WHAT SHOULD I CHOOSE?

I get lost from there cuz after that it shows custum
Kernel Initrd 
then options

then the option to choose the usb 


can you walk me to the process of making the usb boot disk and the installing process?

How hard is to use ubuntu.. i never use any form of linux software

---

### Post by carl4926 on 2010-04-28
I take it then you are working from windows?
You didn't answer me - Can you not use a CD?

Yes I have used unetbootin, but only in Linux.

The options when you first start unetbootin are:
1. To let it download a Linux version from the selection
2. Use a .iso image you already downloaded.

If you choose to let it download a version from it's list, it should do so, and install it to the usb, but it takes a bit of time, it has to download around 700mb

With your usb device connected (disconnect any others)
So at this point: [http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install)
Select the radio button 'Distribution'
Then in the drop box 'Ubuntu'
Then in the version drop box the 'Version'

Ignore the other stuff below
Make sure your usb device is shown at the bottom then click OK

---

### Post by ferjonathas on 2010-04-28
Yes I can use a cd.  I have downloaded the Ubuntu 9.10 and succefully made running boot disk..  
The driver that I sellected was my hd, so I resarted my computer to see if it works...it did i get the boot run fine.. but i got stuck at the commands... I dont know how to ask to run the the wubi file on the cd..

what is the command to open the cd on linux??

like on windows. D:\dir.....

---

### Post by carl4926 on 2010-04-28
You should download the cd .iso and burn it to a cd
Then boot from the cd (You need to make sure that the CD drive is set as the first boot device in BIOS)


What you describe makes no sense to me.

---

### Post by Dayofswords on 2010-04-28
I think your doing it wrong..
(assuming you have the iso, if you dont, dont have? [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) )
[LIST=1]
[*]open unetbootin
[*]click the diskimage radio button
[*]click the '...' or 'browse' on the right of that same row to choose the file
[*]browse to the ISO file
[*]hit open to select it
[*]go to the bottom of the program and choose which drive is your flash drive.
[*]hit ok
[*]burn...
[*]burn...
[*]done
[/LIST]

---

### Post by carl4926 on 2010-04-28
> **tannobrand said:**
> I need help too.  I have no idea what i am doing on this site as well or really how to even use this forum.  Man, i really realize just how computer illiterate I guess I really am.  Someone loaded a counterfeit copy of Windows 7 onto my laptop, and told me it was a legit copy, etc.  Stupid me believed them.  Now, my computer doesn't work at all after error windows came up for last 5 days and says I need activation key or whatever.  I have none.  I basically am screwed.  Now, someone just told me to use Ubuntu.  I went to the website... downloaded it... and this is where I am at now.  Totally confused and need help.  I downloaded Ubuntu on to this desktop, with hopes of then burning a CD (as it says to do)..and then insert it into the laptop that is now not functioning due to counterfeit Windows 7.  Can someone pleeeeeezzzzz help me?  I would be so very grateful.  thank you.

If you get the .iso you downloaded, burned to a cd. Have you done that. It's not clear to me if you have done that.
Once you have a cd of Ubuntu, boot from it
Do you need to recover data from your win7 install.?

---

### Post by ferjonathas on 2010-04-29
Alright I finally got it, it was actually really simple.. i dont know what happened before but i got it installed and running. 
 
anything that i should be aware of ???

---

### Post by ben1986 on 2010-04-29
Yep, as one newbie to another, there are a few things you should know:

Pretty much everything that could go wrong for you will have gone wrong for someone else at some point, and you'll find the answers here, so don't post right away.

Search online for an introduction to the terminal and familiarise yourself with a few concepts, and as a rule of thumb, if you try to do anything (other than use the ubuntu software centre) and it asks for a password, don't do it without googling what it is you're trying to do.

Make sure you know what "sudo" means especially.

Other than that, welcome to the club, your computer just got so much better...

---

### Post by carl4926 on 2010-04-29
Use Software Centre
Search for - Restricted 

And Install Ubuntu Restricted Extras

It's also the easiest way to add applications, especially for a new user

---


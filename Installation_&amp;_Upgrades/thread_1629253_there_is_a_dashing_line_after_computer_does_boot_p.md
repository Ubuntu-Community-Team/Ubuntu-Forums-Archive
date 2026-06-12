---
title: "there is a dashing line after computer does boot procedure, the rest of the screen is"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by npm1 on 2010-11-23
there is a dashing line after computer does boot procedure, the rest of  the screen is black ....i find have to press enter several times before  the the dash becomes small and my OS loads

my system details can be found in my signature

......this is 32bt ubuntu 10.04 with most security updates

---

### Post by sanderd17 on 2010-11-23
If you do nothing, how long does the dash stays there?

---

### Post by sikander3786 on 2010-11-23
> **npm1 said:**
> there is a dashing line after computer does boot procedure, the rest of  the screen is black ....i find have to press enter several times before  the the dash becomes small and my OS loads

my system details can be found in my signature

......this is 32bt ubuntu 10.04 with most security updates
I believe if you don't hit Enter, it would still boot you to the desktop successfully.

How much time does it take to boot if you don't hit Enter?

There have been some issues with plymouth since Ubuntu started using it. My own computer also doesn't like to show the Ubuntu splash, instead it shows the blinking cursor.

---

### Post by npm1 on 2010-11-23
exactly dat but no writing shows....and the dash goes forevver untill i press enter several times the curser truns small then it loads successfully.............
the truth i do not whish to press enter

---

### Post by sanderd17 on 2010-11-23
when you boot, at the point that you are in the grub OS chooser, can you edit the line (I think you need to press 'e', you can read the commands on the window)

if you are in edit mode, at the end, you'll see a word 'quiet splash', delete it. Don't worry to do things in this, it doesn't remember your changes after a reboot.

after you deleted 'quiet splash', boot into is (I think its CTRL+X) and see if the booting keeps hanging somewhere.

Write down the rules on the screen, or take a picture from it and post it here.

---

### Post by npm1 on 2010-11-23
when exactlt do i press e

can i do this from within ubuntu

---

### Post by npm1 on 2010-11-23
by the way after pressing enter a few times it goes into the purple ..... screen loader thingy

---

### Post by sanderd17 on 2010-11-23
you can't do this from ubuntu, that's why you can't make a screenshot of it, you'll have to write it down.

when you boot you computer, you come at a window where you can choose between different OSes. Go to the line where your standard OS is (normally you're already there, so you don't have to 'go' anywhere), press 'e' and you come in some terminal editing mode. Search for 'quiet splash', delete those words and press 'CTRL+X' to boot. 

If you doubt about the commands, there is a little list of possible commands in the bottom of your screen.

---

### Post by sikander3786 on 2010-11-24
> **npm1 said:**
> by the way after pressing enter a few times it goes into the purple ..... screen loader thingy
I am still unable to know exactly about your problem.

If you don't press Enter, does it get stucked? And if yes, at what point does it get stucked? At the blinking cursor...?

For seeing Grub menu, you need to press and hold down Shift key at Bios screen if Ubuntu is the only operating system on this machine.

---

### Post by npm1 on 2010-11-24
ubuntu is the only OS on the new system.....
i think i'll just edit the grub file.....

using these commands

sudo gedit /etc/default/grub
edit the "GRUB_TIMEOUT=10" line and then save and exit. Finally, run
sudo update-grub

before i do that i'll press shift to see what happens

---

### Post by sikander3786 on 2010-11-24
> **npm1 said:**
> ubuntu is the only OS on the new system.....
i think i'll just edit the grub file.....

using these commands

sudo gedit /etc/default/grub
edit the "GRUB_TIMEOUT=10" line and then save and exit. Finally, run
sudo update-grub

before i do that i'll press shift to see what happens
Unless we know clearly about your problem, we are unable to adivse properly. Please consider providing some more information if you want us to probe the problem for you ;-)

---


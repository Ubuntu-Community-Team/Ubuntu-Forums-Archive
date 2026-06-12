---
title: "Reboot / Restart doesn't work"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by daisyflower on 2012-05-15
I had an earlier problem displaying the grub menu.  After a third reinstall, it finally was able to show the grub menu.  However, when it says it has finished, it needs to restart.  It won't restart though.  I have to remove the battery and start it up that way.  If I load Lubuntu and then shut down instead of rebooting, then that works also and I don't have to remove the battery.  Minor annoyance if have to reboot.  Any ideas what to do?

---

### Post by daisyflower on 2012-05-16
This problem still exists.  I cannot select reboot or restart with any success. I have to manually remove the battery from my netbook.  Windows 7 restarts fine.

---

### Post by jadtech on 2012-05-16
> **daisyflower said:**
> This problem still exists.  I cannot select reboot or restart with any success. I have to manually remove the battery from my netbook.  Windows 7 restarts fine.

you cannot select  rrestart or when you  do it shuts down   or it does nothing ???

when you go to the terminal window and type 

```
 sudo reboot


```  
nothing at all happens

---

### Post by efflandt on 2012-05-16
I have an old multiboot desktop (not the one in my sig) that at some point would not properly "reboot".  When it reset during reboot, it would still be running hard drive and fans and everything, but do nothing more.  So knowing that, when something wanted to reboot, I simply got into the habit of shutting down, and cold booting.

Another reason I got into that habit, especially when rebooting to a different OS, is that when rebooting, Windows would sometimes leave hardware (like network cards) in a state that Linux could not deal with, or possibly Linux would leave hardware in a state that Windows could not deal with.

So if rebooting does not work for a particular computer, don't do that.  Shutdown and cold boot instead.  Doing that will update things that ask you to reboot.

---

### Post by jadtech on 2012-05-16
Ubuntu 12.04 can't restart

Issue

Ubuntu 12.04 can't restart following the standard reboot procedure: 

Click system button in upper right corner > Shut down... > Restart button

It ends up in a black screen.

Solution

The reason for the problem could be a BIOS issue or the hardware setup of the system

1) Enter the command in the terminal

```
sudo gedit /etc/default/grub
```

2)** Find ***GRUB_CMDLINE_LINUX=""* and change it to [B][I]GRUB_CMDLINE_LINUX=&#8221;reboot=efi&#8221;
[/I][/B]
3) **Save** the file and run the command:

```
sudo update-grub
```

Reboot :) 

information found here

[http://www.inforbiro.com/blog-eng/ubuntu-12-04-most-common-problems-and-solutions/](http://www.inforbiro.com/blog-eng/ubuntu-12-04-most-common-problems-and-solutions/)

---

### Post by daisyflower on 2012-05-19
> sudo gedit /etc/default/grub

When I enter that, I get, "sudo: gedit: command not found"

Any other ideas?

---

### Post by jadtech on 2012-05-19
you should start reading this documentation  get familiar with this documentation before trying to reinstall again ..

befor you install any software or hardware you have to be familar with the software and hardware that makes your computer run :)

---

### Post by daisyflower on 2012-05-19
I am sorry, I don't understand you.  What documentation are you referring to?  You copied and pasted the pertinent information that seems to be related to my problem.  The other information on the linked page addresses other issues.  Is there a different starting point?

---

### Post by daisyflower on 2012-05-20
I think I might know the reason for this problem.  When I installed, I installed from the USB, so I think it is set to look for a boot option from the USB.  Even though I changed the BIOS in the end to launch from the hard drive of my computer, it might still be looking for USB when it tries to restart.If I am correct, does anyone know how to go about telling it to restart from the hard drive and not look for a USB boot option?

---

### Post by jadtech on 2012-05-20
this thread started by saying you had an issue getting your computer to shut down , it would restart fine but  not shut down .. 

if this is the case everything I can find on this subject and others having the issue it is related to UEFI  which is something Microsoft is using experimenting with as a way to replace bio;s and lock hard drives so other operating systems can not be used or installed .. 
ABOUT 3 OR 4 posts up I posted the solution many are using to fix the problem .. 

if you do look in bios see if there if you can find evidence or something related to EFI  :)

as to what documentation here is just some . 

[http://www.inforbiro.com/blog-eng/ubuntu-netbook-restart-problem/](http://www.inforbiro.com/blog-eng/ubuntu-netbook-restart-problem/)

[http://www.inforbiro.com/blog-eng/ubuntu-12-04-most-common-problems-and-solutions/](http://www.inforbiro.com/blog-eng/ubuntu-12-04-most-common-problems-and-solutions/)

[http://askubuntu.com/questions/127443/new-efi-laptop-after-restart-ubuntu-boots-to-black-screen](http://askubuntu.com/questions/127443/new-efi-laptop-after-restart-ubuntu-boots-to-black-screen)

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by daisyflower on 2012-05-21
In my case, there is no UEFI setting in the BIOS.  There is only 1 HDD, 1 internet boot, and 3 USB boots.  I moved those to the bottom and put the HDD one on the top.

---

### Post by daisyflower on 2012-05-23
Are there other Lubuntu support areas?  I am surprised a programmer working on Lubuntu development wouldn't be interested in troubleshooting this problem.  I have a new Acer netbook and I imagine any other person would encounter the same problem when installing Lubuntu.  ---  It will not reboot, I have to shut down and then turn the computer back on ---

---

### Post by jadtech on 2012-05-23
if you go to terminal window and type 

```

sudo reboot 


``` 

does the computer reboot

here is a copy and pasted from a very old post I found solution to the same problem you describe .. 

see if  either of these solutions work for you 

> If you choose shutdown instead of reboot, does the computer shutdown properly?
Is this a desktop or laptop? Can you post the specs? including the motherboard chipset?
Shutdown / reboot problems are often related to acpi configuration issues. When you boot the computer, hit F6 to add boot options. Type** acpi=off** and boot up. Then try and reboot and see if it reboots ok. If it does, then that confirms that is an acpi problem. You could then try booting with **acpi=force** and see if you can still reboot properly.

 the only other info I can find on this issue no matter how  much I dig including launchpad discuss this issue related to UEFI ,...

---

### Post by daisyflower on 2012-05-24
**UPDATE**

I have given up on Lubuntu, just too many issues I never experienced with Ubuntu, Kubuntu, or Edubuntu.  I am now using Xubuntu, and the same issue exists.

However, instead of UEFI I am seeing "EFI" when the screen loads before the grub menu and before the BIOS settings if I press f2 (delete on other computers).

I went back to the beginning of the thread and tried some commands using GEDIT to modify the GRUB, but it is saying in Xubuntu that I don't have GEDIT installed.

Right now, I don't know how to get it.  I will look into it more and see if there is a solution.

---


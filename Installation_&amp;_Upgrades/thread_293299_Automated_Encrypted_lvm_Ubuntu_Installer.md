---
title: "Automated Encrypted lvm Ubuntu Installer"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by elicriffield on 2006-11-05
[SIZE="3"]
I've been working on an automated way to install Ubuntu onto an encrypted hard drive using lvm.

automated_encrypted_lvm_ubuntu_installer is a shell script that you run from the desktop live cd. What you get is a system where everything on your hard drive is encrypted except for the /boot partition. Even swap is encrypted, its a logical volume too

**The program makes a few assumptions.** 
1. You have only 1 hard drive, or you want to install on your first hard drive.
2. You only want to run Ubuntu, dual boot doesn't work.
3. It should go without saying that all data thats on the hard drive your installing to will be permanently deleted.
4. You have a network connection. (the faster the better, we end up download every package needed. I know it should get them from the live cd, but this way with a few minor tweaks this script could be used to install encrypted Debian from an Ubuntu live cd)

Right now it only does dapper, edgy support shouldn't be to hard to add so I'll probably add it if theres any interest.

What you'll end up with is physical partitions on your desk
1 /boot
2 for hibernate recovery (not really using right now)
3 the physical volume for lvm

LVM is broke out to 
/
/usr
/var
/tmp
/home

The file systems of about the minium size usable. This is so you can install to a system with as low as a 4gig disk. You'll probably need to grow filesystems later. No problem with lvm and reiserfs. For example to make /home 4G do:

```
 
lvextend -L4G /dev/vgcrypt/home
resize_reiserfs /dev/vgcrypt/home

```

Here's How

boot to the dapper-desktop cd (ubuntu-6.06-desktop-i386.iso)
Open a Terminal
Applications -> Accessories -> Terminal
Get the script 
```


ubuntu@ubuntu:~$ [http://eli.criffield.net/auto_cr_inst]("http://eli.criffield.net/auto_cr_inst")
ubuntu@ubuntu:~$ chmod +x ./auto_cr_inst
ubuntu@ubuntu:~$ ./auto_cr_inst


```

Then answer all the questions and it will start installing. It will take a while, at couple hours at best, asking a few questions along the way.

Let me know by replying to this post if anything goes wrong.

Eli Criffield
<cryptoroot AT criffield DOT net> 
[/SIZE]

---

### Post by irw on 2006-11-16
Sounds good, I'll give this a try.

Edgy support would be good - thats what I'm using on my laptop where this would be ideal

---

### Post by elicriffield on 2006-11-16
I started work on edgy support. I doesn't look like its going to take that long I just have to finish it, Theres just a couple things edgy does diffrent.

Eli

---

### Post by kgm on 2006-11-17
> **irw said:**
> Edgy support would be good - thats what I'm using on my laptop where this would be ideal

Yes, it would come in handy here as well.  I'm also using Edgy, and laptops are always going missing these days.

---

### Post by RichJacot on 2006-11-18
Same here.  An Edgy version would be Great!

---

### Post by elicriffield on 2006-11-21
[SIZE="4"]**Edgy Support Added**[/SIZE]

I added edgy support, i haven't tested the new script with dapper, but it should work. The old version is still there, so thats probably a safer bet if your installing dapper.

The script is at [http://eli.criffield.net/auto_cr_inst-edgy](http://eli.criffield.net/auto_cr_inst-edgy) same instructions otherwise.

boot to the edgy-desktop cd (ubuntu-6.10-desktop-i386.iso)
Open a Terminal
Applications -> Accessories -> Terminal
Get the script
```

ubuntu@ubuntu:~$ wget [http://eli.criffield.net/auto_cr_inst-edgy](http://eli.criffield.net/auto_cr_inst-edgy)
ubuntu@ubuntu:~$ chmod +x ./auto_cr_inst-edgy 
ubuntu@ubuntu:~$ ./auto_cr_inst-edgy

```
Answer the questions. You will now have to reboot, login to the console and  run 'sudo /boot/stage_two' to finish the install.

Eli

---

### Post by kgm on 2006-11-30
Worked fine on my laptop, thanks. 
I'm curious what will happen if an updated initramfs-tools gets installed in the future though.

---

### Post by elicriffield on 2006-12-03
> **kgm said:**
> Worked fine on my laptop, thanks. 
I'm curious what will happen if an updated initramfs-tools gets installed in the future though.

It "should" be fine, Though i'd always keep a copy of a known working kernel and initrd file. And rescuing from a bad upgrade should be easy with a desktop cd and the scripts and packages in /boot/crypt/.

If you need to rescue boot to desktop cd
mount /dev/hda1 /mnt
cp /mnt/crypt/rescue_script .
./rescue_script

Eli Criffield

---

### Post by gilrim on 2006-12-15
I've used this guide and script to successfully set up a xfce laptop, and it worked great! I've got a couple of questions tho:

How would I go about to see how much space there's left on the hard drive? I've managed to resize the home partition, but I'd like to know how much more it can be extended.

Second, I'm wondering if its possible to use something like Gnome Partition Editor og QTparted to resize the volumes?

---

### Post by elicriffield on 2006-12-20
> **gilrim said:**
> I've used this guide and script to successfully set up a xfce laptop, and it worked great! I've got a couple of questions tho:

How would I go about to see how much space there's left on the hard drive? I've managed to resize the home partition, but I'd like to know how much more it can be extended.

Second, I'm wondering if its possible to use something like Gnome Partition Editor og QTparted to resize the volumes?

I've never used Gnome Partition Editor or QT parted by anything that supposts LVM and reiserfs would work fine.

from the command line run 
$df -h 

If something needs to grow, run the 
$sudo vgextend -L+1G /dev/vgcrypt/usr
$resize_reiserfs /dev/vgcrypt/usr

Eli Criffield

---

### Post by fitzhugh on 2007-02-12
I spent half a day following really bad lvm directions (or maybe I'm just super clueless) and here I find you did this all for me! Thanks - this is great. I'll give it a shot tomorrow when I've slept.

---

### Post by humbll on 2007-02-23
To Eli: Great script!! Thanks!

To anyone who wants to use this:
- Broadband connection highly recommended.
- Took 3-4 hours with my 3Mbps connection (150-250kBps DSL)
- I installed this on a Dell Inspiron E1505 laptop.
-  [COLOR="Red"]All existing data on the entire primary **hard drive** will be destroyed[/COLOR].
- There is a list of issues at the end that I encountered after the process was complete, one of which is yet to be resolved.
-I have done my best to be accurate with these instructions, but USE AT YOUR OWN RISK. Note that if Eli makes changes to the script then this set of instructions for it may no longer be accurate. I used the Edgy Eft 6.10 release of Ubuntu.

**_Step 0: [COLOR="Red"]Print these instructions!!![/COLOR]_** You will have to reboot several times and you will not have this document to reference unless you PRINT IT!

Step 1: Get Ubuntu [Edgy]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease") or [Dapper]("http://www.ubuntu.com/products/GetUbuntu/download#lts") ISO and burn it to CD. [(How-to burn an ISO in MS Windows)]("https://help.ubuntu.com/community/BurningIsoHowto")

Step 2: [Configure your BIOS to boot from CD first]("http://www.ubuntuforums.org/showthread.php?p=2203844#post2203844").

Step 3: Boot up computer with the Live CD. Choose Option 1 (Run or install Ubuntu).

Step 4: Once Ubuntu is finished loading to the desktop Click Applications-->Accessories-->Terminal.

Step 5: Then type:  **wget [http://eli.criffield.net/auto_cr_inst-edgy](http://eli.criffield.net/auto_cr_inst-edgy)**
*see note in [COLOR="RoyalBlue"]**this color font**[/COLOR] in step 9 if you are not able to download because of no connection to the internet

Step 6: Then type:  **chmod +x ./auto_cr_inst-edgy**

Step 7: Then type:  **./auto_cr_inst-edgy**

Step 8: Then type:  **YES**

Step 9: Do you want to shred the drive? If you have previously stored sensitive data on the drive then you should shred the drive: type YES to this question to shred the drive otherwise just press enter. 

   The script will now download files (after shredding the drive if you typed YES here). 
[COLOR="RoyalBlue"][B]
  *If your network wasn't detected properly on startup, and the script stops, (the following is assuming you are getting internet from a DSL modem, router, or other device which connects to the Ethernet Card) click on System-->Administration-->Networking and inside that box click on Wired Connection and put a checkmark in the box, choose autosetup, then close that box, click on the network connection icon in the tray (an icon of two monitors one behind the other) and chage it from "lo" to "eth0" and goto step 4)[/B][/COLOR]

Step 10: Setup a LUKS password. For decent security use at ***[COLOR="Red"]least[/COLOR]*** a 20 to 30 digit passphrase which includes uppercase & lowercase letters, numbers, and symbols ([Click here for a concise password creation tutorial]("http://www.microsoft.com/athome/security/privacy/password.mspx")). Jot down the passphrase here  (be sure to destroy the paper you write the passphrase on after this is set up if you are truly needing security. [COLOR="Red"]DO NOT FORGET The passphrase [/COLOR]or you will have to start all over again and lose all your data! [Test your passwords here, just type in a prospective password or passphrase and the applet wil tell you how strong it is]("http://www.microsoft.com/athome/security/privacy/password_checker.mspx") (example of a decent passphrase: **My birthday is: 01/30/1901 **  another example: **This is my LUKS pa$$phrase to unlock the drive!**   or this example:   **My dog $pot is 10 years old!**

([COLOR="Red"]caution:[/COLOR] if you screw up retyping the passphrase in step 11 or 12 the script will stop. If this occurs, just continue by typing:   **./auto_cr_inst-edgy**
 (and I think you will be kicked back to step 8 or 10, so be careful re-typing the passphrase..)

Step 11: Type the exact same passphrase from step 10 to verify it.

Step 12: Type the exact same passphrase from step 10 to unlock the drive.
[INDENT]At this point the script will download more files for awhile (15-20 minutes on my DSL)[/INDENT][INDENT] move the mouse every few minutes to keep the screen from going black on you.[/INDENT] 
**[INDENT]Then it will ask you to set up the time zone, and after that it will download more files[/INDENT]**

Step 13: Setup new user: type in a username  (**[COLOR="Red"]CAUTION:[/COLOR]** use lowercase letters - no spaces - nothing fancy, (see example below) or the script will stop and you will have to start over from step 1) Jot the username down here.
[INDENT]example:  **myusername**[/INDENT]

Step 14: Type a system password for the username (USE A [COLOR="Red"]DIFFERENT[/COLOR] PASSWORD than the one you used in step 10) (8 or 10 characters will suffice if you use a mix of uppercase & lowercase letters, numbers, and symbols) example of a decent password:  **2Hard2Crack!**   another example: **Is_This_4_Real?** another example: **Windows_is_4_brainless_librarians!**   another example: **$hut_up_f00L!**  <--in this example I used zeros in place of the letter "o"

Step 15: Type in the exact same password to verify. Jot it down here.

Step 16: Click on System-->QUIT then in the window that opens click Restart.
Take out the CD.

Step 17: [Configure your BIOS ]("http://www.ubuntuforums.org/showthread.php?p=2203844#post2203844")as in Step 2 except now set it to boot from the Hard Drive first. Save & Exit the BIOS. 

Step 18: Your computer will prompt you for the LUKS password. Enter the passphrase you set up in step 10.
Your computer will now boot up to a black screen with white letters. When it finishes booting:

Step 19: Type your username from step 13 and press enter

Step 20: Type your password from step 14 and press enter

Step 21: Type: ** sudo /boot/stage_two**   then press enter

The script will download more stuff now. This will take awhile (2-3 hours on my DSL) if the screen goes black after awhile just press the spacebar to bring the progress screen back. If you get an error at any point and it stops downloading then reboot and start from step 18, the script will pick up where it left off.
After downloading everything then the script will prompt you to reboot the computer, just press the reset button or power button and reboot. You will be prompted for the LUKS password, enter the passphrase you created in Step 10 (you will be required to give this passphrase every time you start the computer)
At the login screen enter the username you choose in step 13...
Then the password from step 14. Be sure to destroy the paper you wrote the passphrase on once you are sure you remember it, especially if you really need this scheme to store sensitive data!. DO NOT FORGET THE PASSPHRASE OR YOU WILL HAVE TO GO THROUGH ALL THIS AGAIN and you will lose the data! Never give out the passphrase or your system password to any1!

Step 22: (OPTIONAL) - (you should subtract 4GB from the size of your hard drive to determine how much you can possibly expand the /home directory, so if your hard drive is 100GB then 100 - 4 = 96GB is the maximum you can substitute for the "5" in the example below) This will enlarge the /home directory, the place where all of your files are stored by default, since Eli made the script do a minimal size for all of the partitions so it would fit on a 4GB hard drive. The commands in **bold **below will make the  /home directory into a 5 GB partition, if you want it larger or smaller just replace the "5" in the first line with the number of GB you want it to be. (Example: If you want 15GB /home directory then you would type:
[COLOR="PaleTurquoise"]**sudo lvextend -L15G /dev/vgcrypt/home **[/COLOR]
in place of the first  **bold** line below, then type the second line as it is shown, you can always use these commands again later to expand it even more if you have extra space, just note that the number of GB you enter here will expand it to a total of that amount, ***not*** add that amount to what is already there):

[B]sudo lvextend -L5G /dev/vgcrypt/home
sudo resize_reiserfs /dev/vgcrypt/home[/B]

Congradulations you are done! Now just install the updates your computer will tell you are available, and any software you want. 
*Also you will eventually need to make the partitions bigger, see previous posts by the author of this script (elicriffield) on page 1 of this thread for more info on how to do this. I will add the info to this how-to as soon as i figure out which partition is which.

If you are working with supersensitive data then you may want to [COLOR="Red"]consider installing truecrypt [/COLOR]and creating a hidden encrypted container with it to store the most sensitive stuff in. Here is the link to my tutorial on truecrypt: [URL="http://www.ubuntuforums.org/showthread.php?p=2205026#post2205026"]http://www.ubuntuforums.org/showthread.php?p=2205026#post2205026
[/URL]
Be sure to thank the author of this wonderful script for his time! Thanks again, Eli! Great job!

[COLOR="Red"]ISSUES I RAN INTO AFTER THE PROCESS WAS COMPLETE AND THE SOLUTION IF AVAILABLE:[/COLOR]

** After installing I was unable to view files on the cdrom drive until i created a mount point for it **by hand by typing in a terminal window (Applications-->Accessories-->Terminal then type:
**sudo mkdir /media/cdrom0**
and enter your system password from Step 14 if prompted.

After the process, I would get a problem with choppy scrolling in Firefox, it turns out to be a display driver problem.

[COLOR="Red"]Unresolved problem:[/COLOR]
When I close the lid of my laptop then come back and open it, there is nothing but a black screen, whereas before (with my original Edgy installation) I would just be prompted for my password and it would load right back into the desktop. Now I have to power off the computer and power back on to get back in.

---

### Post by angrylittleman on 2007-04-08
I am loving this script.  Any chance it can be updated for feisty?  This was just what I was looking for.  Thanks!

Alm

---

### Post by nami on 2007-05-08
what exactly does this tutorial do?  lets say my laptop was stolen and i used this script.  how am i protected, does it make it impossible for the thief to get into my harddrive data?

also, feisty fawn script would be cool as i am planning to upgrade to it on the weekend. :KS

---


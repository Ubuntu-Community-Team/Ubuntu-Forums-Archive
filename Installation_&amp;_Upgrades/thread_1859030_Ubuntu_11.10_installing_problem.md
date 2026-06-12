---
title: "Ubuntu 11.10 installing problem"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by mertergun on 2011-10-13
Hi,

I have an installation problem with ubuntu 11.10, 11.04, 10.10. I tried to install all of them by usb, dvd and wubi but couldn't achive that. When I start to install ubuntu, the screen just shows a black screen with a blinking cursor. The only thing that I can do is just rebooting the computer (Keyboard doesn't work at that moment.). I googled this issue, there are people who deal with the same problem, but I couldn't find anything useful.

Hardware:
ASUS Laptop F50sf
CPU: Intel Core 2 Duo 2.8 GHz
RAM: 4096 MB 
Graphic Card: GeForce GT220M

If there is any missing inf. about hardware, please let me know. Btw, I don't know much about ubuntu, so; while advising a solution, please explain how to do it briefly.
Thank you for your interest.

Mert.

---

### Post by sikander3786 on 2011-10-13
Hi :)

Possibly 'nomodeset' or any other boot parameter like 'noapic' or 'acpi=off' could solve the issue, yet again.

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

The above one is an old post focusing Lucid and Maverick but it used to help with Natty as well and might also with Oneiric.

Please let us know how that goes.

---

### Post by mertergun on 2011-10-13
> 

nomodeset and Wubi Install

While doing a Wubi install, you might not encounter a blank screen  during the installation process but once the installation is complete  and you boot Ubuntu from the HDD, you might notice the same. You don't  need to press the <Shift> key then as you will automatically see  Grub menu after selecting Ubuntu from dual-boot menu. Edit and place  'nomodeset' as stated above. 

After selecting Ubuntu from dual-boot menu, the same screen shows up and can't do anything then. How should I edit 'nomodeset' as mentioned above?

---

### Post by sikander3786 on 2011-10-13
Are you trying to do a Wubi install i.e. inside Windows?

---

### Post by mertergun on 2011-10-13
> **sikander3786 said:**
> Are you trying to do a Wubi install i.e. inside Windows?

I was trying that, but I couldn't edit the boot options(nomodoset acpi). I've created a Ubuntu 11.10 USB and then tried to add "vga=791" and "noacpi" commands. (by pressing TAB, I have a different menu as follows)
[IMG]http://yazaninsan.com/wp-content/uploads/2011/01/ekran-ubuntu-usb-kur-flash-disk-ta%C5%9F%C4%B1nabilir-toshiba-stick-y%C3%BCkle-men%C3%BC-boot.png[/IMG] 
But couldn't install ubuntu again. Screen just shows a black screen. At least, I got rid of the blinking cursor. :P

---

### Post by sikander3786 on 2011-10-13
How was the USB prepared? I mean which application was used? Oneiric being available in Hybrid ISO Images, can be easily burnt to the USB without a single change to the menus etc:

[http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create](http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create)

And it would be a good idea to check your downloaded image against any possible corruption:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mertergun on 2011-10-13
The USB was prepared by "Universal USB Installer". But I'll try this application and share the result with you.

Mert.

---

### Post by 23dornot23d on 2011-10-13
posted on wrong thread ... sorry

---

### Post by mertergun on 2011-10-13
> **mertergun said:**
> The USB was prepared by "Universal USB Installer". But I'll try this application and share the result with you.

Mert.

*************** usb and wubi :D I borrowed a DVD from my friend and your advise(your first reply) worked. Thank you :)

---

### Post by clintiii on 2011-10-13
For me WUBI is giving problem. I tried to install ubuntu inside windows using wubi. at the end of process wubi is giving error "'windowsbackend' object has no attribute 'iso_path'".please help me :(
[IMG][[img]http://www.freeimagehosting.net/t/278d5.jpg[/img]](http://www.freeimagehosting.net/278d5)[/IMG]

---

### Post by sikander3786 on 2011-10-13
> **clintiii said:**
> For me WUBI is giving problem. I tried to install ubuntu inside windows using wubi. at the end of process wubi is giving error "'windowsbackend' object has no attribute 'iso_path'".please help me :(
[IMG][[img]http://www.freeimagehosting.net/t/278d5.jpg[/img]](http://www.freeimagehosting.net/278d5)[/IMG]
Not sure but this would be a better place to post your problem:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by texasboy2084 on 2011-10-13
In order for me to install any version of Ubuntu from cd/dvd after 10.04 i have to do the following:


At keyboard and person icon - press escape
At menu - press F6 and select nomodeset, hit escape again
Move cursor to "install Ubuntu" - You will notice  a long line of words, look for quite splash and delete it.
Press enter


Everything should load if your problem is like mine.  


Once Ubuntu installs it will restart, when you get to the boot menu press "e". Find the line that says quite splash and delete it again. But this time type nomodeset, then press ctrl + X.  Once it boots install your graphics drivers. 

That should be the last time you need to do this.

Edit:

sorry missed your post saying you got it working.

---

### Post by Rogueninja64 on 2011-10-14
I am still having this issue where it goes blank... I have done everything everyone has suggested any other ideas?

booting from usb.

---

### Post by sikander3786 on 2011-10-14
> **Rogueninja64 said:**
> I am still having this issue where it goes blank... I have done everything everyone has suggested any other ideas?

booting from usb.
Hardware specs please, importantly the RAM and the graphics chip make/model.

---

### Post by bkosh84 on 2011-10-14
Yeah, I'm having the same exact problem and can't figure it out. Tried both booting from USB and DVD and nothing is working..

HP Pavilion g4 Laptop with:
AMD A4-3300M 1.9 GHz with Radeon Graphics (integrated)
4GB of RAM
Windows 7 64bit

---

### Post by sikander3786 on 2011-10-14
You might want to try the 'radeon.nomodeset' parameter instead of 'nomodeset'. Please see the section at the bottom of this page named 'nomodeset alternatives for other Graphic Cards' for instructions:

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by bkosh84 on 2011-10-14
> **sikander3786 said:**
> You might want to try the 'radeon.nomodeset' parameter instead of 'nomodeset'. Please see the section at the bottom of this page named 'nomodeset alternatives for other Graphic Cards' for instructions:

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

The problem with that is I don't have the "Other Options" option when I boot the USB Drive.

---

### Post by sikander3786 on 2011-10-14
> **bkosh84 said:**
> The problem with that is I don't have the "Other Options" option when I boot the USB Drive.
Sorry, I should have mentioned it in the first place.

Please burn the USB again, this time following this tutorial:

[http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create](http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create)

The preferred method is to use the command line method if you've got access to another PC running Ubuntu/Linux.

---

### Post by bkosh84 on 2011-10-14
> **sikander3786 said:**
> Sorry, I should have mentioned it in the first place.

Please burn the USB again, this time following this tutorial:

[http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create](http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create)

The preferred method is to use the command line method if you've got access to another PC running Ubuntu/Linux.

I don't have another PC with Ubuntu so I'll try the Windows GUI solution.. If that doesn't work.. Maybe I'll boot Ubuntu 10.04 on my CR-48 and try it that way? I dunno. lol.

---

### Post by sikander3786 on 2011-10-14
> **bkosh84 said:**
> I don't have another PC with Ubuntu so I'll try the Windows GUI solution.. If that doesn't work.. Maybe I'll boot Ubuntu 10.04 on my CR-48 and try it that way? I dunno. lol.
The Windows GUI method should work as well. Don't forget to rename your image from .iso to .img as mentioned there.

---

### Post by bkosh84 on 2011-10-14
Ok. So I used the Windows GUI method and I booted from it.. It showed the purple background (with on windows showing) for about 3 seconds then it showed a command prompt for about one second then the screen went blank... But I heard the Ubuntu sounds after a minute of the screen went blank.. 


EDIT: I got the USB Drive back to 2gb :)

Must not be my day for Ubuntu, lol.

---

### Post by sikander3786 on 2011-10-14
That is a welcome sign that you are hearing the login sound. Means using the 'nomodeset' parameter should work for you, I believe.

So, as soon as your computer starts booting from the USB, immediately after the Bios screen, start hitting any key unless you see the menu that is shown in the screenshot at the link I provided.

You didn't try with 'nomodeset' earlier, did you? If not, first try 'nomodeset' rather than 'radeon.nomodeset'.

---

### Post by bkosh84 on 2011-10-17
Sorry for just now getting back to this, I went out of town for the weekend. I tried both nomodeset and radeon.nomodeset and both of them would show command lines scrolling through and then it would try to load a firmware file and it would take about 15 minutes then just go to a blank screen again... Ugh!

---

### Post by sikander3786 on 2011-10-17
> **bkosh84 said:**
> Sorry for just now getting back to this, I went out of town for the weekend. I tried both nomodeset and radeon.nomodeset and both of them would show command lines scrolling through and then it would try to load a firmware file and it would take about 15 minutes then just go to a blank screen again... Ugh!
Sorry, I too am late in getting back to you on this.

So, did you try the other boot parameters from F6 menu? Try with all of them one-by-one. 'acpi=off' or 'noapic' are the most important ones here.

---


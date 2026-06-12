---
title: "How to download all updates for a certain version"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by alunacast38 on 2011-12-10
Greetings: :D

I am writing this thread because I have Kubuntu Karmic Koala (9.10) on my Sony Vaio Laptop (it is the only version that really work well on it) and I wonder is there is a way to download all the updates to my computer.  I want to be able to burn them into a cd or dvd, in case something happened, like if there is no way to update it in the future from Internet and something happened to my computer.  :(

Could someone help me here?  :confused:

---

### Post by oldos2er on 2011-12-10
Support has ended for Karmic, which means no updates.

---

### Post by dabl on 2011-12-10
There is [APT on CD](http://aptoncd.sourceforge.net/)

However as oldos2er has said, 9.10 is done with support -- what it is today is what it will be forever.

Have you booted a 11.10 Live CD or USB stick, and played around with it?  What kind of issues do you have?  Have you spent any time looking for fixes or workarounds -- I haven't heard of a general "VAIO Incompatibility" problem.

---

### Post by BC59 on 2011-12-10
As @dabl said, I use my Sony-Vaio since 9.04 and I was installing every new version, up to 11.10 I'm using now. Never had the slightest incompatibility problem.

---

### Post by alunacast38 on 2011-12-10
Thank you all for answering.

I have a Sony Vaio VGN-CS320J.  I had played around with both versions, Ubuntu and Kubuntu, 9.10, 10.4, 10.10, and 11.04.  10.4 and up gave me problems with the monitor display of the laptop, it kept blinking, a lot.  Also the Gui, KDE and Gnome, on those versions, seems to not work well, the icons and bars kept moving a lot, from one place to another on the desktop.  I had search for answers on the internet, forums, chats, etc.  It seems like the problem is with the Hardware of this computer.:(  The only one, I don't know why, that works out of the box is Karmic Koala. :)

Back to the thread, I know there is no support anymore, but when I installed this version it did an update from somewhere on the Internet.  I want to know if it is possible to download this updates? (that are old, but are newer than the packages that I have on the CD). :confused:

---

### Post by alunacast38 on 2011-12-10
Ah, also, the versions of 10.4 and up, does not recognize my touchpad, and everytime my computer goes to sleep and/or hybernate, the keyboard does not work, at all. :(  Those are the reasons why I decided to stay with 9.10.

---

### Post by BC59 on 2011-12-10
There is a way to clone your installation. Install Remastersys and use the .iso created, to make a bootable DVD, to have it as rescue disk.

---

### Post by alunacast38 on 2011-12-10
BC59:

I will try what you are suggesting, but Do you meant with that that this process actually copy what I already have installed on my computer?

---

### Post by BC59 on 2011-12-10
Actually there are 2 ways to do it. With Remastersys or Clonezilla.

How to install Remastersys
[http://www.remastersys.com/repository/ubuntu-testing/](http://www.remastersys.com/repository/ubuntu-testing/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) (a little out of date)
How to install Clonezilla
[http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/](http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/)

I use Remastersys and copies everything. In that case you have to remove your personal files before the cloning, to avoid creating a huge .iso file. Then you burn the .iso on a DVD and you can use it as a normal Ubuntu installation disk.

---

### Post by dabl on 2011-12-10
> **alunacast38 said:**
> Ah, also, the versions of 10.4 and up, does not recognize my touchpad, and everytime my computer goes to sleep and/or hybernate, the keyboard does not work, at all. :(  Those are the reasons why I decided to stay with 9.10.

Huh -- the Vaio touchpad and keyboard don't even work correctly on Windows:  [http://www.techsupportforum.com/forums/f108/sony-vaio-touchpad-and-keyboard-not-working-444407.html](http://www.techsupportforum.com/forums/f108/sony-vaio-touchpad-and-keyboard-not-working-444407.html)

In this thread, it indicates that a kernel boot option "acpi_sleep=nonvs" solved the problem for some Vaio models: [http://ubuntuforums.org/showthread.php?t=1586178&page=5](http://ubuntuforums.org/showthread.php?t=1586178&page=5)

---

### Post by alunacast38 on 2011-12-10
Thank you, dabl.

BC59, I download the Ramestersys, but in order to install it I have to delete from it udev, and I do not think I should do it.  So, I am going to try Clonezilla instead.

---

### Post by kio_http on 2011-12-11
Using Kubuntu karmic is a really bad idea.
Its version of KDE is so old and buggy compared to 11.10.

Rather than posting a thread about sticking with karmic, what is your hardware and what problems to you have with 11.10?

---

### Post by alunacast38 on 2011-12-11
Hello, kio_http:

My post was not about sticking with Karmic Koala nor to encourage others to do it, :( but it was about how to download and keep the upgrades from Karmic Koala with me. :)

In the other hand, about the problems that I had encounter using Kubuntu and Ubuntu 10.4 and up...

> 10.4 and up gave me problems with the monitor display of the laptop, it  kept blinking, a lot.  Also the Gui, KDE and Gnome, on those versions,  seems to not work well, the icons and bars kept moving a lot, from one  place to another on the desktop.> Ah, also, the versions of 10.4 and up, does not recognize my touchpad,  and everytime my computer goes to sleep and/or hybernate, the keyboard  does not work, at all.Those are quotes from previous post, but I am going to try to explain what happened exactly...

Everytime that I try to install any version later than 9.10 on my computer the following things happened:


[LIST=1]
[*]After sleep or hibernate, the keyboard does not work at all.  So I was forced to shutdown the computer and restarted it (this happen too with karmic koala).
[*]The screen (monitor) blinks a lot.  The image go away for a second and then comes back.
[*]The desktop environment goes wild.  Things that were supposed to stay in a particular place, move to another.  Example, the panels moving from its original position to another.  Another example, when I opened the Launcher Menu, the menu list never stay where it is supposed to open.
[/LIST]

When I try to fixed the first of them (keyboard problem), the following things happened:


[LIST=1]
[*] After changing the line [GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"]  for [GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"] on the document [/etc/default/grub], the keyboard problem is fixed, but the touchpad does not work at all after that, and it is not recognized by Kubuntu or Ubuntu 10.4 and up. (This fix the problem on 9.10 and does not conflict with the touchpad)
[/LIST]

One thing I noticed recently about the blinking problem, is that it seems to be a problem with the version of the kernel.  I will explain my self now...


[LIST]
[*]I few months ago, I decided to upgrade 9.10 kernel for a new one, that was recommended by the Update Manager.  When I did it and after restarting the computer, the blinking problem was showing in Karmic Koala too!!!! :(  So I had to reinstalled 9.10 again.  :(
[/LIST]


About the Hardware of the computer:



[LIST]
[*]Processor: Inter Core 2 Duo Processor T6500 / 2.10 GHz
[*]Graphics: Mobile Intel Graphics Media Accelerator 4500MHD
[*]Display: 14.1" / 1280 x 800
[*]Total Memory: 4 GB
[*]Storage approx: 320 GB
[*]Model: Sony Vaio VGN-CS320J
[/LIST]

---

### Post by dabl on 2011-12-11
> **alunacast38 said:**
> 
[*] After changing the line [GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"]  for [GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"] on the document [/etc/default/grub], the keyboard problem is fixed, but the touchpad does not work at all after that, and it is not recognized by Kubuntu or Ubuntu 10.4 and up. 

But did you ever try it with

```
[GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"]
```

:confused:

Other Vaio users reported that this fixed the keyboard and touchpad problem.

---

### Post by alunacast38 on 2011-12-11
No, I did not. Why? What does it does? :confused:

---

### Post by Gracie4000 on 2011-12-11
I have an ancient Dell Inspiron 4000 and I am using Lubuntu 11.10-alternate-i386.  It seems to function quite well with my OLD computer.

---

### Post by alunacast38 on 2011-12-15
> **dabl said:**
> But did you ever try it with

```
[GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"]
```:confused:

Other Vaio users reported that this fixed the keyboard and touchpad problem.



I Installed the new Kubuntu 11.10, and I try why you had said but I does not do anything at all!  It does not fix the problem. 

Now I am stuck with a version that does not recognize my touch pad... :(

---


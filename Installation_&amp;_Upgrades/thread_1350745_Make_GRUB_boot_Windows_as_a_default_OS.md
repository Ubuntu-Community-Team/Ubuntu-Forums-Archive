---
title: "Make GRUB boot Windows as a default OS?"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Trifud on 2009-12-09
I have Windows alongside Ubuntu and I would like to make Windows boot in 5 seconds after GRUB has been loaded. How do I do that?

---

### Post by adaucourt on 2009-12-09
> **Trifud said:**
> I have Windows alongside Ubuntu and I would like to make Windows boot in 5 seconds after GRUB has been loaded. How do I do that?

Here is documentation:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Trifud on 2009-12-09
Obviously that information is out of date. For example I don't have a file called menu.list.

---

### Post by darkod on 2009-12-09
Count the position of the windows entry in grub menu.
In terminal open:
sudo gedit /etc/default/grub

Change the value for GRUB_DEFAULT to the position of windows entry less one (if windows is 5th in grub menu put 4).
Change value of GRUB_TIMEOUT to how many seconds you want it to wait

Save and close the file. Run
sudo update-grub

Note: If with an update more kernel entries are added, you will have to change the value for Default again.

---

### Post by gadolinio on 2009-12-09
Go to [http://packages.ubuntu.com/search?](http://packages.ubuntu.com/search?)
In the text box on the upper right corner search for "startupmanager" and choose the package for your version.
Once installed, the application will be in system-->administration-->startup manager.
You'll be asked for your user password.
The application has a list where you can select any of your currently installed OS's to be the default one. And you can also set the time befor booting that default OS.

---

### Post by phillw on 2009-12-09
> **gadolinio said:**
> Go to [http://packages.ubuntu.com/search?](http://packages.ubuntu.com/search?)
In the text box on the upper right corner search for "startupmanager" and choose the package for your version.
Once installed, the application will be in system-->administration-->startup manager.
You'll be asked for your user password.
The application has a list where you can select any of your currently installed OS's to be the default one. And you can also set the time befor booting that default OS.

I got it from Synaptics Package Manager - once you'd given the name for it

That's so cute, it's naughty !!!!

Thanks, that is one heck of a little add-on !!

Phill.

---

### Post by darkod on 2009-12-09
> **phillw said:**
> I got it from Synaptics Package Manager - once you'd given the name for it

That's so cute, it's naughty !!!!

Thanks, that is one heck of a little add-on !!

Phill.

Not to ruin the party but I've seen opinions that it still has glitches working with grub2. It seems well tuned for grub1 but can create issues for grub2. Maybe if you change just some particular settings, don't know.

---

### Post by phillw on 2009-12-09
> **darkod said:**
> Not to ruin the party but I've seen opinions that it still has glitches working with grub2. It seems well tuned for grub1 but can create issues for grub2. Maybe if you change just some particular settings, don't know.

kewl... i can practice repairing grub. I could do with the practice - only ever broke it once (on my upgrade from grub --> grub2)  :p

lol

Phill.

---

### Post by adaucourt on 2009-12-11
> **Trifud said:**
> Obviously that information is out of date. For example I don't have a file called menu.list.

Since you are pointing out the obvious you might have wanted to pay attention to the giant heading that says:
[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=important.png[/IMG] **Note: These directions do not apply to Karmic -- Karmic uses Grub 2. See [Grub2]("https://help.ubuntu.com/community/Grub2") for Karmic.**

---

### Post by Trifud on 2009-12-11
Aham, how do I install GRUB 2 to the boot record of the partition instead of the MBR ...from a live USB flash?

---

### Post by presence1960 on 2009-12-11
> **gadolinio said:**
> Go to [http://packages.ubuntu.com/search?](http://packages.ubuntu.com/search?)
In the text box on the upper right corner search for "startupmanager" and choose the package for your version.
Once installed, the application will be in system-->administration-->startup manager.
You'll be asked for your user password.
The application has a list where you can select any of your currently installed OS's to be the default one. And you can also set the time befor booting that default OS.

+1

Startup manager is a good choice for those not wishing to have Ubuntu be the default since the default OS # is determined by the position in the OS order in GRUB. With every Ubuntu kernel update the Windows entry number will change as it will slide further down in the order and then you will have to edit GRUB again to have windows be default. With start up manager that is not necessary.

---

### Post by meierfra. on 2009-12-11
>  then you will have to edit GRUB again to have windows be default.

This is only true if you refer to Windows by its number. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)".  Then you can use

GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

in /etc/grub/default, and you won't have to edit Grub after kernel updates.

---

### Post by presence1960 on 2009-12-11
> **meierfra. said:**
> This is only true if you refer to Windows by its number. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)".  Then you can use

GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

in /etc/grub/default, and you won't have to edit Grub after kernel updates.

You are the man. I have learned two things about GRUB 2 in two days. I am not trying to suck up, but I feel I have to say this: back about a year or so ago people like you and caljohnsmith really helped me learn a lot from your posts in here. I would read everything I could that you two wrote. I haven't seen you two in here very often lately, but your input is always welcomed.

---

### Post by meierfra. on 2009-12-11
> You are the man.

Thanks for your vote of confidence. But the GRUB_DEFAULT="Windows Vista (on /dev/sda1)" trick is straight from drs205's  [Grub2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by presence1960 on 2009-12-11
> **meierfra. said:**
> Thanks for your vote of confidence. But the GRUB_DEFAULT="Windows Vista (on /dev/sda1)" trick is straight from drs205's  [Grub2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")

I hear you, but most of what is taught we each learned from someone else and pass it on. Some choose to not share their knowledge. So for that I commend you.

---

### Post by darkod on 2009-12-12
> **meierfra. said:**
> This is only true if you refer to Windows by its number. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)".  Then you can use

GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

in /etc/grub/default, and you won't have to edit Grub after kernel updates.

Yeap, thanks from me too. Didn't know that.

---

### Post by guimaster on 2009-12-12
> **presence1960 said:**
> +1

Startup manager is a good choice for those not wishing to have Ubuntu be the default since the default OS # is determined by the position in the OS order in GRUB. With every Ubuntu kernel update the Windows entry number will change as it will slide further down in the order and then you will have to edit GRUB again to have windows be default. With start up manager that is not necessary.

  I just reinstalled Xubuntu 9.10 and I have been searching for an hour trying to find an old thread that explains how to make Windows the default boot with two easy Terminal commands. No installing of Startup Manager or any editing of files.

 The thread is located here: [http://ubuntuforums.org/showthread.php?t=1287414&highlight=grub+2+easy+windows+boot+default](http://ubuntuforums.org/showthread.php?t=1287414&highlight=grub+2+easy+windows+boot+default)

 This thread worked for me before just fine so I want to keep it alive at the top of Google searches. This thread works great for me with XP SP3.

---

### Post by presence1960 on 2009-12-12
> **guimaster said:**
> I just reinstalled Xubuntu 9.10 and I have been searching for an hour trying to find an old thread that explains how to make Windows the default boot with two easy Terminal commands. No installing of Startup Manager or any editing of files.

 The thread is located here: [http://ubuntuforums.org/showthread.php?t=1287414&highlight=grub+2+easy+windows+boot+default](http://ubuntuforums.org/showthread.php?t=1287414&highlight=grub+2+easy+windows+boot+default)

 This thread worked for me before just fine so I want to keep it alive at the top of Google searches. This thread works great for me with XP SP3.

That will work also. That is the power of Linux. For most things we want to accomplish there is almost always more than one way to do so.

P.S actually you did edit a file through terminal. You moved and changed the name of 30_os-prober file. You didn't edit the contents but you edited it's location & file name.

---


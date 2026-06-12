---
title: "[SOLVED] GUI Won't Load after 8.10 Upgrade"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Cheat King on 2008-10-04
Hey, I upgraded from 8.04 to the 8.10 BETA today, but when I rebooted, I was faced with the following message after the Ubuntu logo and loading screen came up. (This was all in the command line.)

```
Starting up ...
[   0.568053] ACPI: EC: GPE storm detected, disabling EC GPE
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/d5dbe3cc-adea-4380-8913-e1abf4427b16) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/d5dbe3cc-adea-4380-8913-e1abf4427b16
kinit: No resume image, doing normal boot...

Ubuntu intrepid (development branch) inphoar-laptop tty1

inphoar-laptop login:
```

This was directly after I upgraded from a clean installation of 8.04, and restarted.

Any help for me?

Thanks in advance.

Big, golden cookie for whoever helps. :^o
Maybe not then...

EDIT: Hmm, found this, do you think it would work? I don't want to muck up my system. [http://www.thekip.nl/2007/12/18/kinit-no-resume-image-fixed/](http://www.thekip.nl/2007/12/18/kinit-no-resume-image-fixed/)

---

### Post by Perfect Storm on 2008-10-04
Thread moved to Intrepid Ibex Testing and Discussion

---

### Post by elmer_42 on 2008-10-04
What it looks like to me (I'm not a Linux guru by any definition of the word) is that for some reason it thinks that it has suspended or hibernated or something, and it's looking for the data it saved before it went into suspension. It can't find it, and then it asks you for a username.

Once you enter your username and password, you'll be thrusted into a CLI system, and you should be able to start up GNOME. I think that running [FONT="Courier New"]startx[/FONT] should work. The original poster in that thread had some more trouble with GNOME, but if one of those commands doesn't work, post back.

I used a minimal install of Ubuntu once, and after I had installed gdm ([FONT="Courier New"]sudo apt-get install gdm[/FONT]), I started it with [FONT="Courier New"]sudo /etc/init.d/gdm start[/FONT]. Then I entered my username and password and selected the window manager I wanted to use. It worked just fine for me.

---

### Post by Cheat King on 2008-10-04
Thanks, I'll see what happens.

EDIT: Sorry, I didn't see this section. I'll look around and see if there is a solution for it here.

---

### Post by inportb on 2008-10-04
> **elmer_42 said:**
> What it looks like to me (I'm not a Linux guru by any definition of the word) is that for some reason it thinks that it has suspended or hibernated or something, and it's looking for the data it saved before it went into suspension. It can't find it, and then it asks you for a username.

It *always* looks for hibernation data before it boots; otherwise, how would it know if you had saved data or not? This part is normal.

The weird part is the login prompt right after that...

---

### Post by jlh68 on 2008-10-04
I also got the same condition as **CHEATKING** did, on my Acer Travelmate Laptop.

What is GPE Storm?

I updated a 8.04LTS system to 8.10 beta.

Now all I have is a black screen with white text and I can not do anything with it.

Question can I repair this if I had a CD with the 8.10 on it?  I do not want to do a clean install as I don't want to loose data, but I do want to get my system running.

---

### Post by inportb on 2008-10-04
GPE == General Purpose Event. Looks like the OS is getting gratuitous GPE's. There is a certain tolerance for more-than-usual GPE's, but the system knows something's wrong when the tolerance is exceeded.

I believe this kernel version has a reduced tolerance compared to older kernels. I had a similar issue with the i386 kernel, but was able to boot normally using the amd64 kernel.

---

### Post by civetta on 2008-10-04
I get the same kinit message. When I try sudo /etc/init.d/gdm restart, it tells me it's restarting gnome. Ok, good... but still no gnome. I try startx and it tells me no screen is recognized.

Anyone have a solution after just upgrading to ibex beta? Just did it last night.

---

### Post by civetta on 2008-10-04
> **civetta said:**
> I get the same kinit message. When I try sudo /etc/init.d/gdm restart, it tells me it's restarting gnome. Ok, good... but still no gnome. I try startx and it tells me no screen is recognized.

Anyone have a solution after just upgrading to ibex beta? Just did it last night.

Ok, seemed to be a problem with xorg:

sudo dpkg-reconfigure xserver-xorg

then things worked again!

---

### Post by Cheat King on 2008-10-04
Hey, I did that before I saw this, and it worked, I think it said to do that in the config file, or something. :p Thanks everyone though, I'll 'thanks' civetta only, if I can't thank anyone that's tried to help me. 

YAY!

---

### Post by davidsrsb on 2008-10-05
I had the same problem, booted in recovery mode and generated a fresh xorg.conf to get my gui back

---

### Post by Cheat King on 2008-10-05
Hey, it works fine now, but I have to log in and then type startx every time I load, is there a way around this?

---


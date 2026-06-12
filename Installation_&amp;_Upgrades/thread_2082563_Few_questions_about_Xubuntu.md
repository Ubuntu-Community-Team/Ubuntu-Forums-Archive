---
title: "Few questions about Xubuntu"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by usingthebuntus on 2012-11-09
I am going to assume Xubuntu is the best choice in my situation.

Kubuntu 12.04 worked fine on an older computer, but it was evident that 12.10 was too much for it.  So, I decided to put Xubuntu on instead, and it loads faster, but it's Xubuntu 12.04.

Now, I am trying to upgrade to 12.10, and I don't see the option to do this.  In Kubuntu I found a way to try to install, but I can't find how to do this.  So here are some questions about getting Xubuntu working.

1. Where are the exact directions for upgrading from 12.04 to 12.10 on Xubuntu?
2. When it loads, I get a yellow note window in the center.  How do I remove this from appearing every time I start the computer?
3. When I installed Xubuntu 12.04, I used a USB, which is 8gb.  However, the hard drive is is much larger.  When it asked about installation, it showed 60GB.  This seems like it would install on the hard drive, but when I start the computer I have to always use the USB stick.

There was no option I saw to install on USB or hard drive, just the mentioning of 60GB.

This problem often comes up when installing Kubuntu and Xubuntu.  It seems like a hit or miss thing, like it randomly chooses if the installation will depend on using the USB or load fine without it.  

Can I change it now to not need the USB stick or do I have to re-install Xubuntu and do something else?  

4. I know there is Lubuntu, but I don't really like it.  I have tried it, but I prefer Xubuntu if I can't get Kubuntu.  So, my question is how much of the resources am I saving by going with Xubuntu instead of Kubuntu?  Then, how does Xubuntu compare to Lubuntu?  How much am I losing if I don't go with Lubuntu and use Xubuntu?

5. This is a shot in the dark, but on Windows you can reduce the resource load to a gray taskbar.  Can you do something like this with Kubuntu?  I would like a light version of Kubuntu on an old computer.  If not available, then I will try to get Xubuntu working.  12.04 is working fine, but I don't know how to upgrade and get the other issues resolved.

---

### Post by Frogs Hair on 2012-11-09
1. [http://xubuntugeek.blogspot.com/2012/10/how-to-upgrade-xubuntu-1204-to-xubuntu.html](http://xubuntugeek.blogspot.com/2012/10/how-to-upgrade-xubuntu-1204-to-xubuntu.html)

Sorry I can't help with the USB issues I use a DVD. 60 Gb doesn't seem right considering my Ubuntu uses under 6. Is that the size of the partition you set up ?

---

### Post by 2F4U on 2012-11-09
3. I guess that during installation you choose to install the bootloader Grub to the USB instead of the hdd. This can be repaired:

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

4. Xubuntu and Lubuntu differ slightly in resource usage, but not as much as one might think. You save between 30 and 50 MB of RAM, but not much with respect to CPU. Personally, I prefer Xubuntu over Lubuntu because it is more configurable out of the box.

When you say your computer is old, can you post your hardware specs? One problem with any Ubuntu distribution is that 12.10 doesn't provide a kernel for non-PAE CPU's, so if your CPU is non-PAE upgrading to 12.10 might be difficult.

---

### Post by usingthebuntus on 2012-11-10
> 60 Gb doesn't seem right considering my Ubuntu uses under 6. Is that the size of the partition you set up ?If it doesn't seem right, then it's not what I was talking about.  The problem, plain and simple, is that it reported the diskspace of my hard drive, but it requires my USB stick to be plugged in in order to boot up.

At NO point in time did it ask to have the grub, bootloader, etc... (whatever you can think of) require the USB stick to be attached to the computer when booting up.

I didn't choose anything of the sort.  It only asked me a few simple things: location, keyboard layout, and to install alongside existing installations or completely over the hard drive erasing everything.  Nothing else.  I didn't go to the advanced settings either.

>  I guess that during installation you choose to install the bootloader Grub to the USB instead of the hdd. This can be repaired:

It never asked to install a bootloader grub to the USB instead of the hdd.  It only asked for:

1. location
2. keyboard layout
3. install alongside or erase HDD 

Then it went on its merry way installing.  I chose nothing to indicate I wanted the USB stick to be needed in the booting process.  If it was part of the installation, then it was part of the installation, and I would hope the programmers would change this to default to the HDD cause it is rather frustrating trying to figure this out and wasting away my weekend.

> One problem with any Ubuntu distribution is that 12.10 doesn't provide a kernel for non-PAE CPU's, so if your CPU is non-PAE upgrading to 12.10 might be difficult.

Again, this is another issue I have with the programmers.  They set it up so by default you don't get updates on new releases.  I had to worm my way through for hours trying to find where the setting was to set it to notify me of updates.

Things like these are time consuming.  _Can we have something out of the box that:_

[B]1) INSTALLS DIRECTLY TO THE HDD AND NOT DEPENDENT ON ANY USB STICK
2) NOTIFIES THE USER OF NEW VERSIONS[/B]

These are 2 simple requests I think the programmers could easily put in so the users aren't fishing around trying to find the solution.  

I am now reinstalling Xubuntu 12.10 from a new download instead of upgrading from 12.04.  Hopefully, this will solve the problem.  But when another version comes out, then maybe I will have the same issue.  I hope not.  Programmers, I beg you to please make it install to the HDD by default without needing the USB stick to be attached when the computer boots after the initial installation and notify users of new versions without making the users fish around for the setting to get the notifications.

To add a third, they decided to make the yellow note window a default.  Why?  Why would you make the yellow note window a default and not notices for upgrades?  It's mind boggling.  So, I had fish around for that setting and uncheck it.  Now I get to do it all over again if this new 12.10 install works.

Each of these things adds hours onto the user's time.  I hope linux programmers realize this and take measures to make it more user friendly.

---

### Post by critin on 2012-11-10
12.04 is the most stable LTS. 12.10 is so new that it will probably give you trouble.  

> It never asked to install a bootloader grub to the USB instead of the hdd.  It only asked for:

1. location
2. keyboard layout
3. install alongside or erase HDD 
[QUOTE]
Then it went on its merry way installing.  I chose nothing to indicate I  wanted the USB stick to be needed in the booting process.  If it was  part of the installation, then it was part of the installation, and I  would hope the programmers would change this to default to the HDD cause  it is rather frustrating trying to figure this out and wasting away my  weekend.[/QUOTE]It does default to the HDD, but if you sat there reading and happened to tap the scroll on the mouse a bit with it sitting on the page, it moved the hdd entry to the usb drive entry.   The drives menu is easy to turn if the cursor was sitting on it.  This is at the bottom of that page, it has text about loading the grub into the hdd drive or you can choose another.  With your finger on the scroll button it's easy to change it without knowing, especially if you're not observant -- don't know it's there,  and don't double check everything before moving on.

Reinstalling grub to the HDD would have been an easy fix.

Exploring the system is the only way to learn where things are.   

The yellow note.  Did you open Tom Notes or sticky notes?   I had one of those open on the screen a few times also.  It's not a default, it's a user issue.

---


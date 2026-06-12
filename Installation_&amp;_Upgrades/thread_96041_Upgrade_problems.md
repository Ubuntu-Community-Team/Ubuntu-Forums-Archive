---
title: "Upgrade problems"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by miguelito928 on 2005-11-28
I've only been fooling around with Ubuntu for a month or so now.  I upgraded to Breezy on my desktop very smoothly.  I also just recently repartioned my laptop and put Ubuntu on it.  I just tried to upgrade from Hoary to Breezy on my laptop, but it didn't go quite the same way and now it isn't working.  FYI: I used the same Hoary install CD for both computers.

When upgrading on my desktop, I just went to Update Manager and changed the repositories to point to Breezy rather than Hoary.  However, on my laptop, I had to first add all the repositories myself (they weren't there by default).  Then after updating, I noticed some of the nice GUI stuff hadn't been installed like on my desktop.  So I went into Synaptic and thought that if I installed the new linux image packages that might do the trick.  Now I'm realizing it was probably some ubuntu artwork or theme package that did all the GUI stuff.

So I'm wondering why the Update Manager didn't get the new linux image like my desktop did.  Also, now when I boot up on my laptop, it shows all the initialization stuff but instead of going to the GUI desktop, it does some text-based login or something.  Can anyone tell me if this is an easy fix?  And also why it doesn't seem to be so automated for my laptop in updating?

---

### Post by miguelito928 on 2005-11-28
oops, posted twice...

---

### Post by miguelito928 on 2005-11-29
Nobody has ever seen this before?  I don't know how to get past the textual login when ubuntu boots up.  Where did my GUI go?

---

### Post by showme on 2005-11-29
I have the same problem.  I logged in using the text mode and then tried entering "gdm."  It returned to the command prompt without any error message.  I would actually prefer logging in this way, however, I would like to be able to use Gnome.  How do I get from the login to Gnome?

---

### Post by invalid on 2005-11-29
Login to the terminal with your username / pass, and then try:```
sudo dpkg-reconfigure xserver-xorg
```

Cheers,
Cb

---

### Post by Topsiho on 2005-11-29
Though this will not help you to resolve your problem (probably "Invalid" gives the solution :) ) I want to react to:

"Then after updating, I noticed some of the nice GUI stuff hadn't been installed like on my desktop. So I went into Synaptic and thought that if I installed the new linux image packages that might do the trick. Now I'm realizing it was probably some ubuntu artwork or theme package that did all the GUI stuff."

The nice GUI-stuff as you write is not in the kernel, which is just (ahem) the heart of your linux system, but is given to you by either Gnome (Ubuntu) or KDE (Kubuntu).

In both Gnome and KDE artists have done their splendid work, but the GUI's are much more than that.

If this makes sense to you:

You might compare (shudder) Linux to MS-DOS and the GUI's to the graphic shell on top of this: Windows.

Now to un-shudder: Gnome and KDE are to Windows as Linux is to MS-DOS: much better. With Gnome having a more lean-and-mean philosophy and KDE is becoming a little bloated. Which does not prevent that I (still) prefer KDE, but  I do not want to start a KDE/Gnome discussion :)

I was a teacher before I retired and I guess it shows. Sorry for that :)

Topsiho

---

### Post by miguelito928 on 2005-11-30
I did the reconfiguring for xserver like you said:

> Login to the terminal with your username / pass, and then try:
Code:

sudo dpkg-reconfigure xserver-xorg


Cheers,
Cb

However, it didn't work.  I went through a bunch of configuration settings and when it finished it took me back to the terminal.  I figured a restart would have me entering the standard GUI desktop, but it didn't.  Any other suggestions?

And does it going into laptop mode mean much of anything?  That's the last thing it does before going into terminal login.

---

### Post by az on 2005-11-30
You did not have the ubuntu-desktop package installed when you did the upgrade, right?

Install that to pull in the missing packages you need.  Usplash is the package that makes your diplay all nice and pretty when you boot.  It has to be installed *before* you install another kernel image.

So, if you are running linux-image-2.6.10-686, you can reinstall it once you have usplash installed.  It will rebuild the initrd to include the usplash.

sudo apt-get install --reinstall linux-image-2.6.10-686

Use the correct linux-image package (386, k7 686, whatever...)

---

### Post by teaker1s on 2005-11-30
check that restricted modules are installed have you tried hitting escape at boot and booting previous kernel in your grub list?

---

### Post by showme on 2005-11-30
From <http://www.ubuntulinux.org/support/ReleaseNotes5.04/> I took the suggestions from the heading "Post Upgrade."  Step 1. is 
```
sudo apt-get --purge remove portmap
```
As soon as I entered this command, it seemed to be restarting the upgrade.  Afterward, I had X-server and Gnome.  
I also tried Step 2.,
```
sudo apt-get install unbuntu-base ubuntu-desktop
```
but the message read that I already have the base and did not have the dependencies for the desktop.
At any rate, I am thankful that my system works better than before Step 1.

---

### Post by Doomed_Tupperware on 2005-11-30
[QUOTE=azz]You did not have the ubuntu-desktop package installed when you did the upgrade, right?

Install that to pull in the missing packages you need.  Usplash is the package that makes your diplay all nice and pretty when you boot.  It has to be installed *before* you install another kernel image.

So, if you are running linux-image-2.6.10-686, you can reinstall it once you have usplash installed.  It will rebuild the initrd to include the usplash.

sudo apt-get install --reinstall linux-image-2.6.10-686

Use the correct linux-image package (386, k7 686, whatever...)[/QUOTE]

Could someone put that in much simpler terms? Do I do the above after I update and I can't get my GUI? I had the exact same problem with my laptop, and also when I go to the update manager it tells me "the following packages are not updated<br><br>linux-image-386<br>linux-restricted-modules-386<br><br>
Any help would be appriciated.

---

### Post by az on 2005-12-01
[QUOTE=Doomed_Tupperware]Could someone put that in much simpler terms? Do I do the above after I update and I can't get my GUI? I had the exact same problem with my laptop, and also when I go to the update manager it tells me "the following packages are not updated<br><br>linux-image-386<br>linux-restricted-modules-386<br><br>
Any help would be appriciated.[/QUOTE]

The above will fix usplash.  To fix your graphical display:

1.  Make sure you do not have half-installed packages:

sudo apt-get -f install

2.  Make sure you have all the neccessary packages:

sudo apt-get install ubuntu-desktop

3.  Make sure that X (the graphical display) is properly configured

sudo dpkg-reconfigure xserver-xorg

4.  And then try starting X

sudo /etc/init.d/gdm restart

---


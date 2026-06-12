---
title: "Graphics issue with 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by RamR on 2010-04-30
Hello all.

When I tried to upgrade from 9.04 to 9.10 back when it was released I had a graphics problem where the login screen would never come up and the screen would go black.  So I just kept 9.04.

Now that 10.04 is out I tried the live CD and the same thing happened.  So I did an upgrade to 9.10 to see if the previous problem had been fixed... and it worked.  Then I went straight to the 10.04 upgrade.  The problem is back.  Now I have figured a way to get around the problem and that is to  boot in failsafe graphics mode... but if I have to do that every time it will be a pain.

Does anyone know of a solution to this problem or am I just going to have to wait to see if it gets fixed like 9.10 appears to have been?

---

### Post by skbhat03 on 2010-04-30
Nothing to worry about. As you stated, it is due to the Graphic problem.

Do the following:

1. When you insert the CD and boot, you will get a screen with a small rectangle (keyboard) and a human figure at the bottom of the screen. When u arrive at that screen, just press any key, space bar will do.
2. You will get the language option, select English and press enter, you will be taken to a screen with options for installation.

3. Make sure the option "Try Ubuntu without any changes" is selected (don't hit enter yet)

4. Now press F6 on ur keyboard.

5. You will see a small pop up on the right hand side of the screen, just hit escape to make it go away. And you can see a long command line which is already there.
Just start typing 
i915.modeset=0 xforcevesa and press enter.

And from there it should work fine :)

Best regards,
Subbu

---

### Post by RamR on 2010-04-30
Great quick reply Subbu.

Does this lead me to a fresh install?  If so, since I have already done the upgrade is there anything I could do to fix the problem while it's already installed?  Or is it better to a fresh install regardless?

Thanks for the help.

---

### Post by skbhat03 on 2010-05-01
I am not very sure about the upgrade.

Let me ask you this, do you get that keyboard and human figure at the bottom of the screen when u r trying to boot ?

If you are getting that, then i suggest you to follow the steps given above. 

If that does not work, fresh installation will work.

Best regards,
Subbu.

---

### Post by Wiebelhaus on 2010-05-01
[Ubuntu-Geek]("http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html")


>  graphic cards to fix this problem try to use the following solution i hope this would help

Solution1

I have a HP Pavilion SLimline s7727c

with lspci giving me

VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

I was getting a blank screen (out of sync) on booting from the live cd.

I worked around the problem as follows:

* At install screen press F6 and select nomodeset and install Ubuntu as usual.
* On first boot after install, press e on getting the GRUB bootloader.
* Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
* Press Ctrl and X to boot
* You should now be able to login to your Ubuntu as usual

For those of you who do not know what to do next, in the taskbar click on System->Administration->Hardware drivers, and select and activate the nvidia current driver if you have an nvidia card like I do. The driver will be downloaded and activated automatically, and you will be prompted for a reboot.

Solution 2

Yes, I think you may be right about it being a graphics card problem. I think you may have the same problem that I did on my beat-up old Toshiba Satellite A10.

So, here is what should work:

At the very first screen, the one with just the rectangle (it’s meant to be a keyboard) and a human figure, press any key - spacebar will do.

Then choose your language.

Then make sure you have “Try Ubuntu without any changes” selected, and then press F6

Add this to the end of the command line:

    i915.modeset=0 xforcevesa

Then press enter and it should boot successfully.

Thanks to [ubuntu forum user]("http://ubuntuforums.org/showthread.php?t=1463294&page=2") for this solution

---


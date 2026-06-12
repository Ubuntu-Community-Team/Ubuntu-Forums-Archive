---
title: "new install on old Dell laptop"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by kirby-u on 2008-11-16
Hi, 
I'm new to ubuntu and also re-formatting. I was trying to reformat my old Dell Inspiron 8200 for ubuntu and ran into a major problem. When it was installing the base, it stopped at "linux-generic" kernel. It won't really do anything now. I know that's the important part. can anyone help?

It did ask me to look at the log at a certain location. I don't know how to do that for more details. 

Thank you for any help. 

Well wishes. 

PS I am using the alternative boot install for i386 since my laptop is so old.

---

### Post by kirby-u on 2008-11-16
I tried to install 8.04 after an un-successful attempt at installing 8.10. 

This time, during the base install, the locales were corrupt, so I went forward without them. And, at 83% of the base install-- just as it did with the 8.10 version attempt-- the 'linux-generic' kernel failed to load. 

Why would the linux-generic kernel fail to load? Would this be a bad burn on the boot CD? Should I just try to burn the image slower? 

Also, can anyone explain to me how to get here:
/var/log/syslog or the virtual console 4 -- in order to see the log for more clues?

What I know about my old laptop:

30 GB hard-drive
old OS: Win XP Pro
256 mb RAM

I have been using the alternate installers for i386 for all of my attempts at installing ubuntu. 

If anyone can offer any guidance, I will be very appreciative. 

Thank you in advance.

---

### Post by D C Ross on 2008-11-19
For what it's worth I just did a clean install of 8.10 on an Inspiron 8200.  I just booted off of the regular CD in the internal drive and ran through all of the usual choices and it ran with no problems.

Once the installer was finished I did have some troubles with power management and suspend mode not working, but aside from that everything was smooth.

If this isn't happening for you then it could be any number of problems.  Your install CD could be bad, so try burning a new one or even downloading a fresh copy if you don't trust the one you have.  Try using the memtest86 option from the installer to check for memory faults on the Inspiron.  There could also be a fault on your hard drive.  See if you can switch to a text console and view the system log during installation.

To view "virtual console 4" hit Alt-Control and F4.  Alt-F7 will switch you back to the graphical display, and the other function keys F1 through F6 will bring up other consoles.  If there's a significant error with your installation it will probably throw a message up there somewhere.

---


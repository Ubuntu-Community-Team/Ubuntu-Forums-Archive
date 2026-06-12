---
title: "Failed ubuntu install"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by urawanker on 2011-12-15
First and foremost I would like to apologize if this has already been posted.  I have searched and could not find the same issue and resolution.  

I have tried to install Ubuntu 11.10 64 bit, both with dual boot windows 7 64 bit, and without.  During the install outside of windows I get "vdevd[109]:timeout:killing 'sbin/mod probe -bv pci:"  followed by a string of numbers.  After some time of these messages streaming down the screen I get "udevadm settle - timeout 120 sec  sys/devices/pci (followed by numbers)" and "020/backlight/acpi-video (1346)".  

I have had some success while installing within windows, but still upon reboot/booting into ubuntu I am greeted by a blinking cursor and it does nothing past that.  I have tried adding "nouveau.blacklist=1" to the install (per another thread), but still cannot get past the blinking cursor.

Machine specs

MB - Asus Maximus IV gene-z z68
video - EVGA GTX570HD
HDD - Seagate 1tb 7200k
RAM - Kingston HyperX Blu DDR3 1333 4x4G
CPU - Core i7 2600k

Thank you, in advance, for any help you can provide.

---

### Post by gordintoronto on 2011-12-15
Did you burn the ISO to a CD and boot from that, or are you installing from a USB flash drive?

Can you run from the LiveCD?

I could be wrong, but "nomodeset" seems more popular than nouveau.blacklist.

There are two articles in the Ubuntu Community Documentation which might help you. The first describes common problems with the CD, and is called BootFromCD, unlikely in your case. The second describes using boot options to handle quirks with your hardware, and is called BootOptions. From what I have seen, one or the other of them solves at least 90% of the problems.

However, there's no question that there are frequent problems with the very latest hardware such as your motherboard and video card.

---

### Post by urawanker on 2011-12-16
gordintoronto,
  
  Thank you for your reply, I started tinkering with it more 1-2 hours after posting this thread.  Got it working 1st try after completely abandoning burning the iso to cd and usb thumb drive, because I had installed the iso on both media 2-3 times with no avail.  I instead opted to install it inside of windows environment by placing the Wubi file in the same folder as the iso and running it.  

  After a reset this did finally get me text on the Grub menu, which before would display no text and after a few moments go to a black screen with blinking cursor.  I inserted nomodeset into the boot options.  Immediately updated drivers and has worked like a dream since.

  Having been away from the linux environment for many years, things have changed a bit. I have also lost my former knowledge on the subject.

  I got this from multiple other threads, and without the help of people like yourself, I would have never been able to install. It's great having a community like this to depend on in case of situations.

  Thank you ubuntu forums.

---

### Post by FLOG51 on 2012-02-01
Hi urawanker

I have been using Windows my whole life and have finally decided to give Linux a try. 

I have a Win 7 Laptop and have attempted an install from CD to Ubuntu 11.10 64bit. Receiving exactly the same errors you outlined.

Would you be able to give me a guideline on what you actually did to get it up and running.
Regards FLOG51

---


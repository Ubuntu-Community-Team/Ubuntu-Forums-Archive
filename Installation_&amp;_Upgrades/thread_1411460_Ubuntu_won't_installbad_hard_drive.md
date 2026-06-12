---
title: "Ubuntu won't install/bad hard drive?"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by walkingheart on 2010-02-20
[COLOR=Navy][SIZE=2][FONT=Lucida Console]*Hello all..I'm new here and have a problem..I've got a computer where Comodo Time Machine totally wiped out the hard drive..Now when I try to boot up it says I have a registry problem..K, I thought I might be able to save my files, etc., by installing Ubuntu 9.04 to recover them..I put in the disk and Ubuntu booted up fine..I first tried to run Ubuntu without any changes to the computer..It keeps scrolling, fast at first then slows down and it says things like 1238.50734 sr 1:0:0:0: [sr0] Add.Sense: No seek complete or the number and beside it buffer I/O error on device sr0 logical block..The numbers started out in the 600's with basically the same thing but with logical block 321537..I tried to do an install, and it did the same thing..Does anybody know what this is and is there a fix or am I just spit out of luck and my hard drive is unrecoverable..I just did the check disk for errors and it found errors in 2 files..What if anything can I do next?? Thanks in Advance for any suggestions*[/FONT][/SIZE][/COLOR].

---

### Post by amsterdamharu on 2010-02-20
You have a working windows machine I assume to burn your cd. Try tinycore linux, it looks like ubuntu live cd has some problems with your hardware (could be videocard not the hd since try ubuntu doesn't do anything with the disk).

If you don't have any CD's but can boot from usb you can use unetbootin to create a bootable usb.

Tinycore needs an internet connection to install a file browser called xfe and you can install an Internet browser called seamonkey with the appbrowser (click on the desktop or press alt tab for the menu and choose appbrowser) click on file -> connect and search for xfe then install the file xfe.tcz. Do the same with seamonkey if you need to browse the Internet (like this forum)

Tinycore is not a good desktop but excellent recovery program if you need a desktop to do your stuff.


[http://tinycorelinux.com/](http://tinycorelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---


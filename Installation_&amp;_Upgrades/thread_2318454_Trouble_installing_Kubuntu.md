---
title: "Trouble installing Kubuntu"
date: 2016-03-26
forum: Installation &amp; Upgrades
---

### Post by revolutionkiteman on 2016-03-26
this is doing my head in.. second day trying to install kubuntu.
done all i should (i think) shrunk 8.1 volume, to create new partition, installed live cd, in the end of many many try of secure boot on/off etc i got the live cd to work, installed to empty partition with sections for boot/swap etc, still will only run with disc in an into live.
soooo after a whole day of tht, this morning i cleared the HD partition again in a final attempt.
this time using a usb, which is impossible to make active until i used cmd line dskpart to do it that way.
the first time i got a window i never saw before, grub, didt say anything, didnt know what to do there so typed exit....never saw it again!
i get a blue screen as usual, with choose operating system, win 8.1 or unbuntu, win runs fine...hate windows!, butu does not, i get the black screen and the file winboot\ wubi thing.
there is no trace of wubi on my system, not in the uninstall prog or even in regedit., so i dont know whts going on now, the live cd did at least run, the usb dont at all.
please, if anyone can help before i launch this laptop out the window!
its an hp laptop 4gb ram, i have left secure boot on now as that did boot the live cd, but now i just get the wubi prob all the time
thank you guys

---

### Post by kc1di on 2016-03-26
can you give us a little more info about the machine?  Video card ?

You may want to run boot-repair also it's found on the live dvd. 
if you do jot down the web page it gives at the end of the run the file stored there give important info that may help.

---

### Post by revolutionkiteman on 2016-03-26
hi kc, video card is intel HD graphics, nothing special
a bit of a change so far, i have got kubuntu installed again, it won’t load from start, just goes to a black blank screen.
if i get the blue screen with choose os, i choose ubuntu  it fails as usual with the winboot wubi error, choose esc to get boot options, f9 boot device options, os boot manager refi ubuntu it loads into grub, advanced options, ubuntu with linux 4.2.0-34 generic recovery,
i will get the recovery menu

ok, some good news.
after running the shell to repair files etc, i then do normal boot, asks for password ''YES’’!, then it will load into the kubuntu desktop, updating software at the moment.
i hope this is the light at the end of the tunnel

ok, sorry for multiple posts but just gotta get this sorted :) i can boot to kunbutu, and it seems to work fine but i have to go through the process above of win boot error/esc/f9/boot options/ubuntu/grub/ubuntu, must be a way around this

---

### Post by SeijiSensei on 2016-03-26
> i choose ubuntu it fails as usual with the winboot wubi error

Are you actually using WUBI? It has been deprecated.  Either install directly to the drive, or use [VirtualBox]("http://www.virtualbox.org/") for Windows and install Kubuntu into a virtual machine.  I have a dual-boot machine with Kubuntu in a VM on the Windows side, and Windows in a VM on the Kubuntu side.

---

### Post by revolutionkiteman on 2016-03-26
no not at all, done various deep searches on the windows side and its not on the machine at all, at least i have kuby now and its working fine apart from some freezes and crashes, but those probs will be for another forum i guess.
its mainly now trying to get it to boot well without the hassle of all the diff screens n key presses

---

### Post by mansonfan78 on 2016-03-26
The boot loader that linux installs is Grub, it's (by default) a black screen with white text.  A blue "choose os" screen is the Windows boot loader.  So, you're system is loading the Windows boot loader, which sees Ubuntu, but can't load it properly.  Did you install to a different partition on the same drive or to a different drive?  If it's a different drive you just have to change the boot order in your computer's bios and then it should load the Grub menu.

---

### Post by Bucky Ball on 2016-03-27
*Thread moved to **Installations and Upgrades**.*

... and took the liberty of changing your thread title to something that tells potential helpers something about your issue, both of which will increase your chances of support.

---

### Post by revolutionkiteman on 2016-03-27
thanks bucky,
@mansonfan78, in order, switch on laptop, usually get a black screen with the win boot-wubi error, press esc to get boot options, then f9 to get to the setup menu, arrow key down to the ubuntu file then enter.
then the grub screen where i can select ubuntu and it all runs fine from there.
been using all night and apart from freezes, and some crashes which i can&#8217;t report as the debug info extras won&#8217;t download? it runs very well, if it was more stable i would wipe windows completely
thanks for any suggestions guys.
if i use the console in maybe python, is there a way to see a log of the complete startup process? maybe that would be a way to find the prob? just a thought
oh forgot, its a partition on the same  hd

---

### Post by revolutionkiteman on 2016-03-27
yipeee, solved it, in part thanks to mr manson :) when you get so hung up with a problem you seem to get in a rut, although i changed the bios i didnt in th os menu move unbutu up.
now to sort the bug sending problem

---


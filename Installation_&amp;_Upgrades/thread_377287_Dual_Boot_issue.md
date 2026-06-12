---
title: "Dual Boot issue"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by Chopperman on 2007-03-05
It seems I might have posted something a bit more advanced than Beginner's talk is ready for. :) Feel free to dump/merge or whatever to whichever version seems to need it. 

--------------------------------------------------------------------------------------


I have had a very pleasant Ubuntu experience thus far. For a week now I have been running 6.10 32 and 64bit versions on a new hard drive on my HP DV9010us laptop. I had the windows HD pulled out while I got Ubuntu running and was waiting on the mountkit so I can have two drives (windows dedicated and linux dedicated)

Because I enjoy the media boot play features I understand I have to have the windows bootloader handle the OS selection.

I followed (generally) the instructions at: [http://pervasivecomputing.net/ubuntu...inspiron_e1505](http://pervasivecomputing.net/ubuntu...inspiron_e1505)

Where I deviated was:

I booted to 32bit ubuntu and did the linux.bin creation as sudo in the terminal window.
I copied the 512k file to an SD card (linux and windows work well with the built in reader)

After copying linux.bin to the C: drive and adding the bootloader entry in Boot.ini, I do get the OS selection menu as expected, but when I select Linux, the screen blanks and I am left with a single flashing "_" in the upper left corner of the screen. The only input I can do is the three finger salute to reboot.

When I examine the linux.bin file in notepad, it appears to be just whitespace, no random ascii like I would expect in a binary file.

The article does mention booting to a command prompt using a disk called RPL which I am totally clueless about.

SO - is booting with that disk necessary? or should the terminal window creation of linux.bin work? What should the linux.bin look like if I open it in a text editor to confirm that it is correct(er)?

Any thoughts are of course appreciated

Cheers
Chop

---


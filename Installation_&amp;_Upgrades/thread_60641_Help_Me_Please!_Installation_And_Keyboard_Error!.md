---
title: "Help Me Please! Installation And Keyboard Error!"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by ConnorP on 2005-08-28
so i burnt the cd and started installation..then when it went to retrieve some pre-installation files, it said it couldnt find them!

so i restarted and put the CD in my top CD drive to see if it would work, but when i tried to start up..it said that there was a keyboard error or no keyboard was detected...

 ](*,)  ](*,)  ](*,) 

i use a USB keyboard and mouse, any help is appreciated!

*edit* im sorry i dont have much info...any ideas i greatly appreciate!*edit*

---

### Post by scoon on 2005-08-28
Hey there, 

Could be one of 2 things.  First, check your bios.  Some bios have a seeting to turn off/on usb keyboards,  Second, did you check the md5sum of the iso you downloaded to make certain it is correct.

regards, 

scoon

---

### Post by ConnorP on 2005-08-28
[QUOTE=scoon]Hey there, 

Could be one of 2 things.  First, check your bios.  Some bios have a seeting to turn off/on usb keyboards,  Second, did you check the md5sum of the iso you downloaded to make certain it is correct.

regards, 

scoon[/QUOTE]
 the sad thing is i cant check anything....

because

my keyboard doesnt work (>_<)

---

### Post by scoon on 2005-08-29
Hey there, 

Well that does NOT have anything to do with linux.  The bios feeds whatever os you run info about your hardware.  

regards, 

scoon

---

### Post by ConnorP on 2005-08-29
[QUOTE=scoon]Hey there, 

Could be one of 2 things.  First, check your bios.  Some bios have a seeting to turn off/on usb keyboards,  Second, did you check the md5sum of the iso you downloaded to make certain it is correct.

regards, 

scoon[/QUOTE]
 im sorry...but would a non-USB keyboard work better?

and...

how do i check the md5sum to make sure its right?

---

### Post by scoon on 2005-08-29
Hey there, 

If you got your iso from here: [http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/) then if you scroll all the way to the bottom there is a file called MD5SUM.  Get that as well, and then if you are already running linux, you can type md5sum NAME_OF_ISO_YOU_DOWNLOADED.iso and whait for the md5sum to get calculated.  Compare that with what is in that MD5SUM file.  If they match, you are good to go.  If they don't, the iso is broken.  

Would a non-USB keyboard be better ?  Don't really know.  Maybe your kb's are messed up.  I use USB kb's with no problem whatsoever.

regards, 

scoon

---

### Post by ConnorP on 2005-08-29
well my USB KB worked on my laptop..but not on my regular computer..im gonna try a non-USB board and see what happens..

and i think my processor might be an AMD....i downloaded the i386 version..could that cause the install to not work? 

Ty,

connorp

---

### Post by scoon on 2005-08-29
Hey there, 

You really need to have a handle on your hardware (ie: what you have).  If you are a 32bit amd then you x386 is what you need.  If you are 64bit amd then you got the wrong thing.  

regards, 

scoon

---

### Post by ConnorP on 2005-08-29
[QUOTE=scoon]Hey there, 

You really need to have a handle on your hardware (ie: what you have).  If you are a 32bit amd then you x386 is what you need.  If you are 64bit amd then you got the wrong thing.  

regards, 

scoon[/QUOTE]
 ok..
thanks for ur support.

im gonna try the different keyboard and see what happens!

and.srry for asking this..

but how do u know if u have the right thing? will the installation not start or will there be an error? i have an AMD ATHLON XP

---

### Post by duminas on 2005-08-29
[QUOTE=ConnorP]ok..
thanks for ur support.

im gonna try the different keyboard and see what happens!

and.srry for asking this..

but how do u know if u have the right thing? will the installation not start or will there be an error? i have an AMD ATHLON XP[/QUOTE]
 Athlon XP processors will work fine with the i386 version of the install.
To be frank, that's the only one they'll play nice with. XD

---

### Post by ConnorP on 2005-08-29
[QUOTE=duminas]Athlon XP processors will work fine with the i386 version of the install.
To be frank, that's the only one they'll play nice with. XD[/QUOTE]
 hey thanks..

i appreciate ur response and i hope everything works out..

about downloading MD5SUM, is that all i need to download along with the .iso? and what folder should i put it in? Exact file name that i should download? (sorry for so many questions, i just want to get it right as soon as possible)

and im probably going to burn the image at a slower speed to make sure there wasnt a burning error.

---

### Post by majikstreet on 2005-08-29
Hi ConnorP,
I just wanted to say hello and good luck-- I was attracted to this thread because _my_ name is Conor!

How funny!

Anyway, good luck and hope you enjoy Ubuntu Linux!

majikstreet/Conor

---

### Post by duminas on 2005-08-29
All you need is the MD5SUMS file and the .iso.
What you do is, open up the MD5SUMS file in a text editor, such as Notepad or gEdit (depending on OS).

If you have Linux, then you simply issue:
[font=Courier]md5sum <iso_filename>[/font] at the terminal, and compare the value given to what you see in the MD5SUMS file.

If you have Windows, you can get a program called **md5summer** to generate the md5 for you, or you can download the md5sum program from [here](http://downloads.activestate.com/contrib/md5sum/Windows/md5sum.exe) and stick it in C:\Windows, open the Command Prompt, then issue [font=Courier]md5sum <iso_filename>[/font] similarly to Linux.

You -should- be able to use a full path, that is, something like [font=Courier]md5sum "C:\Ubuntu-i386.iso"[/font] (not the actual name of the file, of course). If not, you'll need to change directory to where the file is located.

---

### Post by ConnorP on 2005-08-29
im posting from Ubuntu right now!

Yesssss...

thanks everybody, i really appreciate it!

---


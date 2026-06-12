---
title: "can't install under wine"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by caver1 on 2010-03-29
Since Lucid i can't install anything under wine. No matter what the program I get the following error message.
     "The file '/home/horgnorgle/Desktop/NuancePDFReader_English.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."
You can replace NuancePDFReader with anything

so I read further and
      " Software in Ubuntu needs to be "executable" (sometimes called "trusted"), both in the sense that the software is a program, and that it is marked as an "executable file" via file permissions. Normal software is available for installation via the Software Center; this is the primary source of software in Ubuntu.

Files downloaded from other locations are not marked as "executable" since they did not get installed via a trusted software repository. Because of this, attempting to open downloaded files that are software will fail. The primary reason for blocking this software is to help unsuspecting users avoid malware (i.e. malicious software like trojan horses, worms, and viruses). "

      So how do I get other programs marked as trusted so I can run them
or has Ubuntu under Lucid decided that it knows better than me?

---

### Post by mc4man on 2010-03-29
You could chmod it from the cli or quite simply - r. click - properties - permissions - and set execute for the owner

If the prog installs a desktop icon then do the same on it (will appear as a text file till you do so

---

### Post by caver1 on 2010-03-30
That works fine on a program that is on your harddrive.
If you have an installation cd you can't change permissions as they are read only.
Never had this problem before Lucid.

---

### Post by bolucpap on 2010-03-30
Try typing ```
wine cmd
``` from the terminal. Now you will find yourself in a kind of MS-DOS shell environment. Go to the directory of the program you want to run, and try entering the .exe name from there. I think that will work.

---

### Post by dino99 on 2010-03-30
> **caver1 said:**
> That works fine on a program that is on your harddrive.
If you have an installation cd you can't change permissions as they are read only.
Never had this problem before Lucid.

is it a Lucid problem or a wine one ?
on my end, i'm using the latest wine 1.1.41 on multiple OS without trouble.
So i think you have not the required rights to install.

Anyway, you'd better post on Wine forum, this one is for Lucid only.

---

### Post by mc4man on 2010-03-30
I think it may be a lucid issue - depending on when you installed lucid.
Atm (beta 1+) lucid will not write fstab entries for cd/dvd drives, the media will mount to /media/<volume label>.

So wine can't detect the drive and you won't have permission on /media/<volume label> anyway (at least here.

Here I only use wine for Imgburn which I set the IO to ASPI so drive detection is outside of wine and there are no issues.

As a test wrote a fstab entry for my /dev/sr0 drive, created /media/cdrom0 and wine detected the drive and could open the Setup.exe on COD, either from cli

wine D:/Setup.exe

or directly from browsing the disk - r. click on the Setup.exe - open with wine..

On my other drive with no fstab, wine can't find the drive and the r. click resulted in the *exact error* as the OP noted in post 1

So maybe try creating /media/cdrom0 and adding a fstab entry for the drive ( and then autodetect drives in winecfg

---

### Post by Yfrwlf on 2010-04-01
Confirmed that this is an issue with Lucid Lynx.  While wine cmd and then navigating to D: did work and I was able to run programs that way, doing it directly from CD via Nautilus did not work.

---

### Post by arnab_das on 2010-04-01
this actually is a problem indeed. however the problem is only with wine 1.1.41

i never liked this version (i have used it in 9.10) as most of my games simply refuse to run. my suggestion is, go for 1.1.31, which was the 'stable' (as in beta 'stable' :D) version in 9.10. this problem will be resolved. i have faced the problem described here in 10.04 and ever since i switched/downgraded to 1.1.31 the problem seems to have gone away.

---

### Post by Yfrwlf on 2010-04-13
> **arnab_das said:**
> this actually is a problem indeed. however the problem is only with wine 1.1.41

i never liked this version (i have used it in 9.10) as most of my games simply refuse to run. my suggestion is, go for 1.1.31, which was the 'stable' (as in beta 'stable' :D) version in 9.10. this problem will be resolved. i have faced the problem described here in 10.04 and ever since i switched/downgraded to 1.1.31 the problem seems to have gone away.

Damn, says it will break things when you try to install the 1.1.31 package in 10.04. :P  Yay for cross-distro-version breakyness!  Not!

And of course in 10.04 you're offered Wine (version 1.1.42) or Wine Beta (1.1.42).  AWESOME SELECTION lol

---

### Post by CoolMaxUK on 2010-04-13
Having the same problem here. This essentially renders WINE completely useless and will thus annoy many users out there.

I read on some ubuntu page that they are doing this to prevent malicious programs etc. I thought Microsoft were the ones that limited usability to to stop viruses, not Linux!

Are there any ways of disabling this?

---

### Post by mc4man on 2010-04-13
> Are there any ways of disabling this?
That I wouldn't know

> This essentially renders WINE completely useless 

Well not really, though certainly not as many choices as before.

If you run from a terminal then there should be no issue w/ wine /path/to/.exe
Ex.
wine  /media/COD1/Setup.exe

Now if you have a multi disk install then having wine detect the drive would allow using a win. command and you could just eject with the drive button, insert next disk ect.
Ex.
 wine  D:/Setup.exe

( without drive detection then for multi just use 
wine eject

Other options would be to insert the disk, get mount name and configure a drive letter in winecfg - /media/<volume label>
(too much of a pita

Otherwise if you create an fstab entry and mount dir. (/media/cdrom0 ), then things go back to normal as far as wine.


The only possible issue there is lucid isn't using fstab for cd/dvd drives, so any downside I'm not sure of. ( though haven't noticed any as of yet in a tester.

The one 'oddity' with an fstab entry is the permissions on data cd's and data dvd's - screen 1 cd's, scr. 2 dvd's - don't know what to make of the displayed 'owner' difference. (permissions are the same

---

### Post by mc4man on 2010-04-14
Fairly simple workaround if wishing to open a .exe by clicking on in nautilus. ( and no fstab entry

The default r. click 'open with wine windows program loader' will enforce the 'Security/ExecutableBit policy (whether it should on cd/dvd's is debatable

Just create a new launcher - r. click on the .exe, open with other application -> use a custom command
for the command this will do.
wine

Then either r. click - open with wine or r. click - properties - open with and set the default to wine - then a d. left click on any .exe will work.

Edit:

because of how worthless this security bit deal is - to revert the "open with wine windows program loader" to what it should be...

```
gksu gedit /usr/share/applications/wine.desktop
```

In the .desktop look for line Exec= and change to this, save and close

```
Exec=wine start /unix %f
```

---


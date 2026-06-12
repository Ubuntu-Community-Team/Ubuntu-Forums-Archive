---
title: "Can't burn ISO.  To big"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by The Pinny Parlour on 2010-04-30
Hello

Having issues burning ISO image in win7 to CD.

Have tried 2 different burners, 3 different discs and 3 different burning programs.  All come back with errors.

MD5 checksum is correct so I'm not sure what the deal is.

Am downloading Alt and normal versions again to try.

---

### Post by slvr42 on 2010-04-30
How big is the ISO and how big is the media you are burning to?  CD-R's can only take up to 700MB and DVD's are typically 4.7G.

---

### Post by The Pinny Parlour on 2010-04-30
CD.  ISO file is a tad over 699MB.  
CDBurnerXP says it's to big 702MB.
Windows 7 in-built just errors.
InfraRecorder errors as well. (in addition it kills ones desktop icons in win 7)  Had to uninstall to get icons back.

---

### Post by Youresorock on 2010-04-30
Try burning the CD iso to a DVD disk.  I always do this because DVDs burn so much faster.  It doesn't matter that the ISO is intended for a CDR.

---

### Post by slvr42 on 2010-04-30
A cd won't hold more than about 650 in reality.  If it's anywhere close to 700 you are going to have to burn it to a dvd, if you are trying to create a boot disk.

---

### Post by dandnsmith on 2010-04-30
You (OP) need to look at your CD's, the CD device capabilities, and also the burner constraints.
I have some CD's rated at 800Mbytes - the norm is 700.
Some burner progs allow you to burn 'outside the record zone' - there will be a parameter to set for this.
Some devices will support the 'extended' data use - but you'd have to check it.

In summary, the tip to use a DVD is well worth considering, especially if you don't have the details for the CD stuff readily to hand.

---

### Post by TBABill on 2010-04-30
I'm in agreement with others. If you can get your hands on a blank DVD, just use that. I have done that with many distros after running out of CDRs and it works fine. Your computer won't care as long as it can read and write to DVD-R.

---

### Post by lavinog on 2010-04-30
Which ISO are you trying to burn.
You could try an alternate install if you are just looking to install ubuntu.

---

### Post by The Pinny Parlour on 2010-04-30
Okay all thanks for the replies.

I did re-download both the alt version and the the normal version. 
the alt version is slightly smaller (689mb) compared to the normal version.  The alt version burnt okay to CD but still the normal 699.44mb won't burn.

Having said all that I will use a blank DVD.  

Thanks all for your assistance.  :)

---

### Post by psusi on 2010-04-30
Make sure you are burning it as an image, not a normal file.  If it does not fit it is probably because you are trying to burn it as a normal file, which tries to wrap the file in another iso filesystem and burn that.

---

### Post by ruies on 2010-04-30
Same problem here. Tried different burners on a Win7 machine for both 10.04 32 bits and 64 bits. Get the message they are to big. Had the same problem with 9.10.  "Overburned" it but the disk became unusable. It really irritated me and I ended up not installing Ubuntu on that machine. You cannot call it a CD if it doesn't fit. I think a lot of people will get irritated on this subject. I will now move my burner to an Ubuntu machine and try to burn it there to see if there is differences...

---

### Post by eltonw on 2010-04-30
Another alternative is to use a rewritable DVD, or ... perhaps better: use a USB stick. HOWTO instructions HERE:[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
Under windows you will need to get this:[https://help.ubuntu.com/community/BurningIsoHowto#Windows]("https://help.ubuntu.com/community/BurningIsoHowto#Windows")

---

### Post by P4man on 2010-04-30
+1 for making a bootable USB key instead of a cd/dvd. Its much faster and you dont waste blank discs. Its also *easier*. Just use this:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It will make the usb key for you in like 2 clicks. Even download ubuntu if you dont have the iso yet.

---

### Post by The Pinny Parlour on 2010-04-30
> **psusi said:**
> Make sure you are burning it as an image, not a normal file.  If it does not fit it is probably because you are trying to burn it as a normal file, which tries to wrap the file in another iso filesystem and burn that.

I can assure you, I'm burning it as an image.

---

### Post by dandnsmith on 2010-05-02
I've just downloaded the 32bit desktop version, and burned it to one standard 80min/700MB CD - no problem.

---

### Post by Synackfin on 2010-05-02
Get yourself a 2GB flash drive and download a copy of Unebootin. It will actually allow you to download 10.04 straight from the app, or you can install the ISO right to the drive.

Check it out:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Nick.Sth on 2010-05-02
Are you trying to burn the Ubuntu .ISO file onto a disk? If I recall correctly thats 699mb :P.
If so, try using "Infra-recorder", it's the one suggested on the Ubuntu home site itself!
Here are some simple instructions:
[B][I][FONT=Courier New]https://help.ubuntu.com/community/BurningIsoHowto
[/FONT][/I][/B]
[FONT=Courier New][B][I]And here you Can Download it:
[http://infrarecorder.org](http://infrarecorder.org)[/I][/B][/FONT]
[FONT=Courier New]***[http://sourceforge.net/projects/infrarecorder/files/InfraRecorder/0.50/ir050.exe/download?use_mirror=kent](http://sourceforge.net/projects/infrarecorder/files/InfraRecorder/0.50/ir050.exe/download?use_mirror=kent)***[/FONT] (Actual Download Link)

Hope this helps.

---

### Post by irkregent on 2010-05-03
Every time I download a Intel Desktop ISO, the result is 733 MB (not the 699 MB shown on the web page), which of course does not fit on a CD.  Not sure what's going wrong.
&#9660;
&#9650;

---

### Post by P4man on 2010-05-03
> **irkregent said:**
> Every time I download a Intel Desktop ISO, the result is 733 MB (not the 699 MB shown on the web page), which of course does not fit on a CD.  Not sure what's going wrong.
&#9660;
&#9650;

Dont confuse megabyte with mebibyte.
[http://noppatech.wordpress.com/2008/11/07/mb-to-mib-and-gb-to-gib-conversions/](http://noppatech.wordpress.com/2008/11/07/mb-to-mib-and-gb-to-gib-conversions/)

699 Mib = 733Mb

Its just that many people still use the wrong notation.

---

### Post by ruies on 2010-05-08
I moved my external burner to my Ubuntu machine and burned it there. Solved the problem.

---


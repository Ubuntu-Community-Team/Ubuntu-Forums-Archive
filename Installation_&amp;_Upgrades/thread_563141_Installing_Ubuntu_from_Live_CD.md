---
title: "Installing Ubuntu from Live CD"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by working_night_owl on 2007-09-29
I have tried to install Ubuntu Fiesty with a Live CD but I am having problems with the speed. When I boot from the CD and choose to "Start Ubuntu and Install" it takes at least 5 or 10 minutes for the computer to even start up Ubuntu. Even worse is, when I click to Install Ubuntu, the Install Window will pop up about 10 or 15 min later but window doesn't display the startup process until almost an hour. When I click the first option which is to choose which Language, it again takes over an hour to get to the next screen. I finally just gave up since it was taking so long. Is this normal for a Live CD or should I do something else? My computer is only a couple years old and I have 256 MB of RAM on my computer, could this be my problem?

---

### Post by Pumalite on 2007-09-29
256 MB RAM> Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by working_night_owl on 2007-09-29
So you are telling me that the Live CD is worthless then and I need to install over the Internet?

---

### Post by Pumalite on 2007-09-29
You have to download a new iso from the link I gave you.
Follow these guidelines:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by working_night_owl on 2007-09-29
I requested the CD from the Ubuntu website and got the Live CD through the mail. I didn't burn it using a .iso file. You think creating my own CD would be better then using the Live CD.

---

### Post by Pumalite on 2007-09-29
You need a system with a lighter Desktop; that's why I gave you the link.

---

### Post by working_night_owl on 2007-09-29
Ok I downloaded the Infra Recorder and am using this Recorder to download the mirror of Ubuntu from that link you gave me. Hope it works out alright.

---

### Post by Pumalite on 2007-09-29
Good luck.

---

### Post by working_night_owl on 2007-09-29
Well I burned the .iso to a CD using Infra Recorder and it said it burned successfully. When I tried to boot from the CD though, a error came up saying "NTDetect not found Press Clt + Alt + Del to restart"

---

### Post by apunc1 on 2007-09-29
did you burn the iso as data or a disk image? it needs to be burned as a disk image.

is your computer set to boot from cd? if not, you may need to change the boot order in your bios.

---

### Post by Itchmecho on 2007-09-29
also did you MD5 SUM? it is in that little Howto section... did you do that?

---

### Post by Pumalite on 2007-09-29
[http://www.techspot.com/vb/topic17684.html](http://www.techspot.com/vb/topic17684.html)
[http://www.techspot.com/vb/all/windows/t-17684-NTLDR-is-missingpress-CtrlAltDel-to-Restart.html](http://www.techspot.com/vb/all/windows/t-17684-NTLDR-is-missingpress-CtrlAltDel-to-Restart.html)
[http://www.hardwareanalysis.com/content/topic/19004/?o=60](http://www.hardwareanalysis.com/content/topic/19004/?o=60)
[http://www.hardwareanalysis.com/content/topic/19004/?o=160](http://www.hardwareanalysis.com/content/topic/19004/?o=160)
[http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=24023](http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=24023)
[http://www.pcreview.co.uk/forums/thread-93084.php](http://www.pcreview.co.uk/forums/thread-93084.php)
[http://forum.pcmech.com/showthread.php?t=155981](http://forum.pcmech.com/showthread.php?t=155981)
[http://forums.techguy.org/all-other-software/496788-ntldr-misisng-press-ctrl-alt.html](http://forums.techguy.org/all-other-software/496788-ntldr-misisng-press-ctrl-alt.html)
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

---

### Post by working_night_owl on 2007-09-29
I don't know. The InfraRecorder doesn't ask. I just click the Action tab, Burn image and choose the .iso file. As far as booting from the CD, I did go to the boot setup and choose to boot from the CD but I just get that error after I do.

---

### Post by apunc1 on 2007-09-29
> **working_night_owl said:**
> Well I burned the .iso to a CD using Infra Recorder and it said it burned successfully. When I tried to boot from the CD though, a error came up saying "NTDetect not found Press Clt + Alt + Del to restart"

if the previous suggestions don't work, google that error message and there are many articles about how to repair your hard disk, if that should be the problem.

---

### Post by Pumalite on 2007-09-29
See post # 12

---

### Post by working_night_owl on 2007-09-29
Well I tried to open the CD and check the contents and it doesn't even register that I have a CD in my drive. So obviously it didn't even burn correctly. I am thinking of just going to the Ubuntu website and just downloading the alternate CD program. Should I open it with InfraRecorder also?

---

### Post by Pumalite on 2007-09-29
You can download ImgBurn: [http://www.imgburn.com/](http://www.imgburn.com/)
Install. Go to Mode>ISO>Burn

---

### Post by working_night_owl on 2007-09-29
Well I gave up on the .iso file so I deleted it. I am going back to the Ubuntu website and downloading the alternate text file. Does this also need to be opened and burned to a CD using InfraReader or is this opened some other way?

---

### Post by Pumalite on 2007-09-29
You can use InfraRecorder or use ImgBurn as I told you. The most important thing is that you do md5sum on iso, bur at 4x, and burn as an 'Image' and not as data.

---

### Post by working_night_owl on 2007-09-29
How do you md5sum on iso and where is the option in InfraRecorder to burn as a Image and not data?

---

### Post by Pumalite on 2007-09-29
Follow these guidelines:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by working_night_owl on 2007-09-29
Yes that is what I did last time but it doesn't tell you how to ms5sum a iso file or how to swtich from image or image file option

---

### Post by Pumalite on 2007-09-29
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
And yes it tells you clearly how to burn an Image.

---

### Post by working_night_owl on 2007-09-29
Yes I understand how to burn the image but where is the option to make sure that it is burned as a image file and not a data file.

---

### Post by working_night_owl on 2007-09-30
I can't even find the alternative ubuntu file I downloaded. Was I suppose to save it to disk or just open the file when downloading the file? I choose to just open it when it prompted me what I wanted to do to download the file. It shows up in my list of downloaded files but I can't find it anywhere on my computer though when I do a search. Do I need to download again only this time save it to disk?

---

### Post by Pumalite on 2007-09-30
Normally Downloader in FireFox saves it to Desktop (to disk)

---

### Post by PmDematagoda on 2007-09-30
Have a look in your Browser options, the location for downloads must be given there.

---

### Post by working_night_owl on 2007-09-30
Ok I can locate the files from there. so how do I locate this file when I try to burn it to CD with InfraRecorder. What file paths do I take to locate the downloaded files.

---

### Post by PmDematagoda on 2007-10-01
Just go to the exact location as shown on the web browser, using Nautilus or Konqueror.

---


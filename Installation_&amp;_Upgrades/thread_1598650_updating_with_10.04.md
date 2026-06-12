---
title: "updating with 10.04"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2010-10-16
hi all,

i have decided to stay with the 10.04 LTS.
i currently open office 3.2.0 with this install.
although the 3.2.1 version has been out for some time now, it doesn't show in my update manager.
how can i update this ?
in the future will updates for firefox, chrome etc be shown ?

i hear there are some really nice features in 10.10. also very usefully the boot and shutdown times are much lower than 10.04.

i mainly use the internet, word processing, and see movies/ music.
does this usage justify shifting to 10.10 ?
or would it be a better idea to wait for the next LTS ?
after all the stability of this LTS 10.04 should increase, right ?

thanks!

---

### Post by sandman6471 on 2010-10-16
[B]I know that when you install Google Chrome it ads the repository to your software source list. So Chrome will get updates just like the rest of the system. As far as Ubuntu 10.10 being slow on boot up and shut down, it seems to be pretty quick on my two computers a desktop and an Acer netbook(running desktop version). I mostly surf the internet, word processing, and some spreadsheet work once and awhile, watch streaming video's and of course check out the forums, and some video converting. I was running Mint 9 before and 10.10 seems to hold it's own. 

Linux is Great.....
Take Care Everyone....[/B]

---

### Post by TBABill on 2010-10-16
Lots of quirks and wireless/video issues reported on the forums. Look at the stickies for 10.10 and do some searches for what others have reported. I reverted 2 machines recently but others have had fantastic results. Seems very hardware sensitive/specific right now but those things will get sorted with updates I'm sure. I will wait till it's been out and has some major updates, but a LiveCD may help you decide.

---

### Post by AM_SOS on 2010-10-17
thanks sandman6471!
TBABill, actually i've just decided to check out 10.10 using the LiveCD function.
and i think you are spot on. every time since 9.10 i've noticed teething problems with new version that hit the block every 6 months.
so while they are of course updated with the latest "sexy" features on offer, i now think that its better to go for stability and quality of connection in terms of the OS, browsing experience etc.
in fact, i have just begun a phd and i think i cant afford to be playing around with my system every 6 months.
from the point of view of such academic work, do you think that i will lose out on anything substantial if i decide to stick to the current LTS release?
i am sort of worried about not getting the latest versions of software that allows me to use the internet, multimedia and movies, word processing etc.
what say?
thanks!

---

### Post by sandman6471 on 2010-10-17
IHO, I think you stay with what works best for you. Not sure what software your running that you would want to update. You could always do manual updates on the software that you felt needed to be updated. 

As for me, I like solving problems, or trying to. I was running Mint 9 and never had a problem. So I figured I'd try Ubuntu 10.10, so far it's all good.

In short I don't think you would miss anything important by staying with what you have. You can always catch the next release.

Linux is Great.....
Take Care Everyone.

---

### Post by AM_SOS on 2010-10-17
hi sandman 6471,

two quick queries -

-ok, the really important program i use are Firefox, Chrome, OO Writer, and VLC.
if i stick to the LTS version will i be automatically informed of version upgrades ?
this is my only real worry.
e.g. i just noticed that although OO is offering 3.2.1 on their site, mine is still 3.2.0 and update manager doesn't even offer me the newer version!
so basically if i stick to 10.04 LTS will i have to keep using the old versions of all the above mentioend softwares ?

-i think i am still running the ext 3 file system. will it create problems if i try to upgrade to the next LTS version in 2 years from now ?

thanks!

---

### Post by sandman6471 on 2010-10-19
I know that when you install Google Chrome, it automatically ads a repository to your source list. So your chrome updates are nothing to worry about, you will get them along with your system updates.As far as Firefox you can go through "PPA". Here is a link to a forum here in Ubuntu forums.[http://ubuntuforums.org/showthread.php?t=279213](http://ubuntuforums.org/showthread.php?t=279213). As far as Open Office goes, I found this site, it may be of some help I'm not sure.   [http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html](http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html). 

Well, hope I've been some help to you. Like I said I'm no Linux expert. Good Luck in what ever your decision is.

Linux is Great.....
Take Care Everyone....

---

### Post by sandman6471 on 2010-10-19
I forgot about VLC. This again you would go through "PPA". Here is a site that [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) might be helpful. I updated vlc like this when I was running Mint 9, it went pretty smoothly no problems encountered.  Good Luck....

Linux is Great......
Take Care Everyone.....

---

### Post by AM_SOS on 2010-10-20
hey thanks sandman.
this has been quite helpful.

i checked the VLC link and they suggest that LTS users should update manually. so what doesthis mean ?

is there some way in which 10.04 LTS will automatically update VLC, firefox, open office to the latest versions ?

i am wondering - even if i continue to use VLC 1.0.6 , how does it matter ? i mean my movies, music etc will play fine right ?
so maybe i needn't even worry about updating VLC till ubuntu send out an update.

one final and important query - if i start using the latest software versions for firefox, openoffice, VLC etc could this create compatibility problems ? i mean they are programmed to work with ubuntu 10.10 , right ?

thanks !

---

### Post by snowpine on 2010-10-20
> **AM_SOS said:**
> is there some way in which 10.04 LTS will automatically update VLC, firefox, open office to the latest versions ?

one final and important query - if i start using the latest software versions for firefox, openoffice, VLC etc could this create compatibility problems ? i mean they are programmed to work with ubuntu 10.10 , right ?

10.04 was released April 2010 and all of its applications are "frozen" at their stable version as of that date. You will never get new versions of applications (with a few exceptions, like Firefox) through the regular Ubuntu Update Manager process, but you will get bug fixes and security patches to the existing versions.

You are correct to worry about installing newer applications from outside the Ubuntu repository. Newer applications may have new bugs and may cause stability issues because they have not been tested in 10.04. My personal philosophy is that, if my web browser browses the web, my word processor creates documents, my video player plays movies, etc. I do not care whether they are the newest version or not; I would prefer they are reliable and stable.

That being said, 99% of the time, installing a newer app from a trusted source won't cause any major problems. The PPA system is very popular with many users who want the latest version of a specific application. You can also of course always grab the latest version directly from the developer's site (videolan.org, openoffice.org, mozilla.org, etc). And there is an Ubuntu Backports repository that gives you newer versions of some applications.

---


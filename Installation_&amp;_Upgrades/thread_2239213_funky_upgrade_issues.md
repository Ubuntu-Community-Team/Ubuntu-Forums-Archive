---
title: "funky upgrade issues"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by crs501 on 2014-08-12
While on the pdate Manager yesterday I tried upgrading to the new Ubuntu 14.04.1 and somewhere in the middle of the upgrade it froze. I was unable to do anything but shut down and restart my PC. When I did I was not able to do much. The only installation CD I have is from 8.04 LTS and when I installed that and tried to begin upgrading out of it I was unable because od out-dated software repositories. (I hope somebody somewhere is understanding this mess!) What I would like is to get back to the fully functioning 12.04.5 which I had before this whole episode. ***_HELP!!!_***

---

### Post by ajgreeny on 2014-08-12
One possible way you could go from there is to use the 8.04 live system to download the .iso of 14.04.1 to a USB drive and then still using the live system make a live USB system to another USB drive which you can use to install 14.04.1.

However, can you boot to a command-line with your current OS, or use Ctrl+Alt+F1 to get to a command-line tty?  If you can, you could try ```
sudo apt-get -f install
``` to try to mend any broken packages, and ```
sudo dpkg -configure -a
``` to try configuring any packages that were interrupted before the upgrade was finished.

---

### Post by crs501 on 2014-08-13
Tried the suggestions but can't get that to fix it either. Had a thought - Is there any way I can get Ubuntu 12.04.5 on a CD that I could then install on my PC and get back to work? If this is possible I'd appreciate someone letting me know how I should go about obtaining such a disc. Thanks for reading. 

PS: I also have now learned not to post duplicate threads. I understand that now!

---

### Post by kansasnoob on 2014-08-13
The Ubuntu 12.04.5 downloads are here:

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

But the 12.04.4 downloads are still there too and you don't want those or you'll end up in [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL") hell.

And the 12.04.5 iso images use the Trusty HWE so I'd think you'd be just as well off to install 14.04.1 since they use the same kernel and X-stack. Please take time to look at this thoroughly:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Particularly this:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule)

I have some older hardware that doesn't play well with the Trusty kernel and X-stack so I use the archived 12.04.1 images which still use the original Precise kernel and X-stack which are supported until April 2017:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

But be sure to avoid the 12.04.2 and 12.04.3 images!

---

### Post by crs501 on 2014-08-14
OK, at the risk of repeating myself, if you've read my original post here then you know I'm presently working off of Ubuntu 8.04 which I have re-installed from a disc, I've has since it was new! I have tried all the 'command-line' and 'online download/upgrade/whatever' fix suggestions some of you have offered BUT Nothing is working. When I run Update Mgr from my present 8.04 all I get is *"repositories no longer available"*. And when I try to accept the Upgrade to 10.04 LTS that is offered the process begins but then shows messages such as:* "packages not found", "Failed to fetch" *and *"some index files failed to download"*. The ONLY thing I believe would solve my problem and get me back to work is obtaining the last OS I had been using very successfully - **_Ubuntu 12.04.5 LTS. IS IT POSSIBLE TO OBTAIN THAT ON A DISC???_**  If so, how to I go about requesting it? And is there any charge? Can anybody assist me in this way? Right now I am stuck and extremely frustrated, Can't find a way to go forward and have limited use of what I do have. I would really appreciate some HELP here!! Thank you. Richard...

---

### Post by Dennis N on 2014-08-14
If you want to purchase an installation disk, there are ads on [http://distrowatch.com/](http://distrowatch.com/) 
In fact, I see one on the left side of their main page under "Linux media". Go there and click through so they get some ad revenue and check it out.

---

### Post by mörgæs on 2014-08-14
Crs510, please calm down. People are indeed helping you. 

What you saw was a failed upgrade, not a failing 14.04.1. The best advice is, as people have already mentioned, a fresh install of 14.04.1. Up to you whether you want to buy the disc or burn it.

---

### Post by grahammechanical on 2014-08-14
No one seems to have posted this link.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Basically, you need to change the 8.04 repositories to 10.04 repositories but they have been moved when 10.04 reached end of life. So, you need the new address.

This link might explain it better than I

[http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

Regards.

---

### Post by crs501 on 2014-08-14
* TO: **Grahammechanical**:  Thank you for those links. I checked them out and then did get on a Terminal to try the codes that were recommended (very carefully I might add). Alas, no luck at all, the dialog simply referred me to taking other actions I wasn't really sure about, nor how. So I'm back to looking for a way to order/buy a disc to install from.  I received a link from **Dennis N** but once there I only got the message that access to that server was forbidden. **Morgaes** I am calm, thank you, but nonetheless still frustrated. I'm trying everything and none of it is working. If anyone out there would simply point me to a site or phone number where I could order/buy a disc to install from, I believe my problem would be fast on the way to being solved. Now, who can give me *that* kind of help?

---

### Post by kansasnoob on 2014-08-14
In the US some public libraries even have discs. If they're loaner discs be sure to [enter the advanced boot options]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options") and run Check disc for defects before proceeding though.

---

### Post by crs501 on 2014-08-15
I'm going to try to mark this thread as SOLVED. I have become aware of a site - [www.osdisc.com](www.osdisc.com) - where apparently I can buy an installation disc of Ubuntu 14.04.1 LTS for $5.95 plus $2.65 mailing costs with delivery in 3-5 days. If any of you know of a better solution please let me know here. Otherwise I will be placing my order as soon as I get paid! I want to thank all who did actually try to help me, I really appreciate the Forum and all of you who share your knowledge with all the rest of us.

---


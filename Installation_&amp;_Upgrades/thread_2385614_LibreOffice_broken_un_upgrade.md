---
title: "LibreOffice broken un upgrade"
date: 2018-02-22
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2018-02-22
Ubuntu 17.10
Anyone else having this problem after the upgrade today? 2-22-2018
All information at the top is just little squares.
Thanks in advance.

---

### Post by tinylagarto on 2018-02-22
Which version of LibreOffice is this in your case?

```
apt cache policy
```

will give the output from a terminal.

---

### Post by bob brazie on 2018-02-22
Can't tell without the help menu.
apt cache policy returned : E: Invalid operation cache
It was the newest up grade to Ubuntu 17.10 this morning.

---

### Post by #&amp;thj^% on 2018-02-22
You can use either:
```
apt policy libreoffice
```
or:
```
apt-cache policy libreoffice
```
But not:
```
apt cache policy libreoffice
```
Note the absence of "-"
EDIT: BTW have you tried installing:
```
sudo apt install libreoffice-style-human
```
I can confirm what yours looks like and this worked for my case.
Fingers crossed. :)

---

### Post by bob brazie on 2018-02-22
```
libreoffice:
  Installed: (none)
  Candidate: 1:5.4.5-0ubuntu0.17.10.1
  Version table:
     1:5.4.5-0ubuntu0.17.10.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security/universe amd64 Packages
     1:5.4.1-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe amd64 Packages
```

What is this sudo apt install libreoffice-style-human

Something is broken or it broke something with this update.

---

### Post by #&amp;thj^% on 2018-02-22
> **bob brazie said:**
> 
Something is broken or it broke something with this update.
Yes I get that! ;)
> **bob brazie said:**
> 
What is this sudo apt install libreoffice-style-human

For the Screenshot i just uploaded!
Mine looked Identical to yours>>>until I installed what I mentioned in my previous post.
Just my small effort to help.
EDIT: Just found this also: [https://askubuntu.com/questions/987792/libreoffice-toolbar-icons-went-blank-after-application-hanged](https://askubuntu.com/questions/987792/libreoffice-toolbar-icons-went-blank-after-application-hanged)
Both fix's required a change with the themes being used.
Anyway Good Luck

---

### Post by bob brazie on 2018-02-22
Tried sudo apt install libreoffice-style-human but nothing changed.
I can't do it as the other post mentioned as I cannot open options as all of the file/edit/history etc are just little squares that do nothing. It that post it was the icons that were not showing that is not the case with my problems.

---

### Post by bob brazie on 2018-02-22
I did open the options and changed the view using the alt f12 keys and nothing changed.

---

### Post by vasa1 on 2018-02-22
Try a clean profile in case that helps.

Close all LibreOffice programs.

Rename ~/.config/libreoffice to something else. Restart LibreOffice and see if your problem goes away.

---

### Post by #&amp;thj^% on 2018-02-22
Sorry about that, I guess I'm just lucky.
There seems to be some new changes coming in now Today.
Seeing a few more LibreOffice threads than usual and Bugs also.
vasa1 seems to have a great suggestion in post#9
That might be why I was lucky then...I always use a clean profile when problems arise. 
Stay Tuned! ;)

---

### Post by tinylagarto on 2018-02-23
> **bob brazie said:**
> Can't tell without the help menu.
apt cache policy returned : E: Invalid operation cache
It was the newest up grade to Ubuntu 17.10 this morning.

My bad. I was typing it wrong. My brain was not in sync with my writing. 

But the others corrected it.

---

### Post by bob brazie on 2018-02-23
Gave that a try and it did't help with the commands at the top. Still little squares.

---

### Post by #&amp;thj^% on 2018-02-23
Seems we have at least one user reporting better results with adding a PPA source.
[https://ubuntuforums.org/showthread.php?t=2385634&page=2](https://ubuntuforums.org/showthread.php?t=2385634&page=2)
Some folks don't like adding PPAs to the mix.
Important: it is highly recommended to remove libreoffice before upgrading to the PPA's version. (Currently @ 1:6.0.1~rc1)
If you decide to go this route first:
```
sudo apt remove --purge libreoffice*
```
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
sudo apt upgrade
```
Poster's issue was slightly different than yours but worth a shot.

To revert: use PPA purge

```
sudo apt install ppa-purge
```

Then remove the PPA
```
sudo ppa-purge ppa:libreoffice/ppa

```
Then update:

```
sudo apt update
```


Note: this will uninstall packages provided by the PPA, but not those provided by the official repositories.
PPA-PURGE&#65279;&#65279;: ppa-purge will reset all packages from a PPA to the standard versions released for your distribution.  So basically its like a way to restore your system back to the way it was before you installed packages from a PPA.

---

### Post by bob brazie on 2018-02-23
I will be gone for the weekend but back Monday.
Can we continue this at that time?
Thanks in advance. Bob.

---

### Post by vasa1 on 2018-02-23
> **1fallen said:**
> Seems we have at least one user reporting better results with adding a PPA source. ...
Add me to the list although I've done so in a VM running 18.04.

---

### Post by #&amp;thj^% on 2018-02-23
> **bob brazie said:**
> I will be gone for the weekend but back Monday.

Well have a great time of it then!
> **bob brazie said:**
> 
Can we continue this at that time?

I'll be around when you return. ;) Hoping to see this [SOLVED]
@vasa1 thanks so much for your added support and suggestions.
Best Regards

---

### Post by bob brazie on 2018-02-26
So I ran:

sudo apt remove --purge libreoffice*
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
sudo apt upgrade

Now I need to re-install libreoffice?

---

### Post by #&amp;thj^% on 2018-02-26
> **bob brazie said:**
> So I ran:

sudo apt remove --purge libreoffice*
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
sudo apt upgrade

Now I need to re-install libreoffice?

Yes that's correct!

---

### Post by bob brazie on 2018-02-26
Since I did an update and upgrade earlier what is the terminal input to install libreoffice again?
Hopefully this will solve that problem. <g>
Thanks in advance.

---

### Post by #&amp;thj^% on 2018-02-26
Just like we uninstalled it. (Except Different ;))
```
sudo apt install libreoffice
```
And Yes Hopefully it will Solve It. :)
If not we have one more trick to try.

---

### Post by bob brazie on 2018-02-26
Thanks lots! That seems to have worked. Re-booted and it is still working!!
Out of curiosity what is the one final trick we could have tried>

---

### Post by #&amp;thj^% on 2018-02-26
> **bob brazie said:**
> Thanks lots! That seems to have worked. Re-booted and it is still working!!
Out of curiosity what is the one final trick we could have tried>
It seems that apparmor was causing the mess in the first place and the upgrade to LibreOffice 6 has the new working apparmor profiles.
But Congrats on being a libreoffice user again...WOOT! :D
The other workaround **which I don't like to mention now **is telling apparmor to ignore the profiles, and that's not good. ;) (Safety above All)
If your still curious just PM me, as I don't want the code to be executed with no good reason to... by future visitors. (Hope that makes sense)
Best Regards

---

### Post by bob brazie on 2018-02-26
Thanks again. I think we will leave at that as you suggest.
Have a great week!
Bob.

---


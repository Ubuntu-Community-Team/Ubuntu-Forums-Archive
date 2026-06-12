---
title: "upgraded to 16.04, can't add  new software"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by lila on 2016-08-26
Hi, 

after a failed upgrade, I ended up doing a fresh install with the 14.04.1 DVD I had lying around, and then all the updates and when that was done the upgrade to 16.04.  

Now I'm trying to put back a small number of programmes I use that aren't in the default install.  Starting with Gimp.  The "ubuntu logithèque" (sorry, that's the French name - it's the programme - to - install - programmes whose icon is an orange shopping bag with an A on it, by default in the bar) tells me there is no such programme as gimp.  I don't like logithèque and looked for synaptic, but that also cannot be found.  But logithèque looks badly configured: it tells me the total number of available programmes is three, two of which are already installed (Firefox and something else).  I can't scroll further down to see if there are others.  

So, is this a mere question of activating repositories?  Even without that, three available programmes just doesn't sound right...

---

### Post by oldos2er on 2016-08-26
Did you run ```
sudo apt update
``` first? If you already did that, please post the output of ```
cat /etc/apt/sources.list
```

---

### Post by lila on 2016-08-26
ok, did sudo apt update, it tells me it is up to date.

Did the other one, and get this: 
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

---

### Post by oldos2er on 2016-08-26
You have the universe repository enabled, which is where gimp is. I'd try a command line install: ```
sudo apt install gimp synaptic
``` in case it's a problem with "logithèque." If there is an error please copy and paste all the terminal output here.

---

### Post by mook765 on 2016-08-26
Download the new release 16.04.1, burn a DVD or create bootable USB, install...
That is what ian-weisser and oldfred meant with "fresh" install...
[https://ubuntuforums.org/showthread.php?t=2335131](https://ubuntuforums.org/showthread.php?t=2335131)

---

### Post by lila on 2016-08-28
> **oldos2er said:**
> You have the universe repository enabled, which is where gimp is. I'd try a command line install: ```
sudo apt install gimp synaptic
``` in case it's a problem with "logithèque." If there is an error please copy and paste all the terminal output here.

I'll try that later tonight, thanks.  I even had the idea myself over the weekend, but this saves me searching for the exact code... :P

---

### Post by lila on 2016-08-28
> **mook765 said:**
> Download the new release 16.04.1, burn a DVD or create bootable USB, install...
That is what ian-weisser and oldfred meant with "fresh" install...
[https://ubuntuforums.org/showthread.php?t=2335131](https://ubuntuforums.org/showthread.php?t=2335131)

Yes, I know... the problem being that my other computer has a bug (which is why I wanted to upgrade the good one first, it's the important one).  This bug means it does not create any iso images on CDs, DVDs or usb.  And it's not me, I have no problem doing it on the other one, it's just this one says it's doing it and then the stick or DVD does not work and is recognised as either empty (DVD) or containing an empty folder (usb).  You also cannot delete anything of a usb-stick with this computer, it just stays there.  You can put it in the recycling bin, but you can't empty the bin and when you read the stick with another computer, the thing you deleted is still there.  So I was thinking of doing a fresh install for this second computer anyway.  I guess I should have covered my back and made a new DVD with the better working computer before trying to upgrade that one... Next time, I'll be wiser!  Meanwhile, I improvise to clean up the mess!

---

### Post by RobGoss on 2016-08-28
> 
[COLOR=#000000]after a failed upgrade, I ended up doing a fresh install with the 14.04.1 DVD I had lying around, and then all the updates and when that was done the upgrade to 16.04. [/COLOR]


Why didn't you just do a fresh installation of 16.04. from the start, why install 14.04 and then upgrade to 16.04 I'm just trying to see the logic behind that

Is it because you could not download the ISO file for 16.04 and burn it to a DVD or USB?

---

### Post by lila on 2016-08-28
> **RobGoss said:**
> Why didn't you just do a fresh installation of 16.04. from the start, why install 14.04 and then upgrade to 16.04 I'm just trying to see the logic behind that

Is it because you could not download the ISO file for 16.04 and burn it to a DVD or USB?

Yes, that's it, I think you asked the question while I was typing the answer for essentially the same question posed by mook765
I can download the files, but not burn them.

---

### Post by lila on 2016-08-28
> **oldos2er said:**
> You have the universe repository enabled, which is where gimp is. I'd try a command line install: ```
sudo apt install gimp synaptic
``` in case it's a problem with "logithèque." If there is an error please copy and paste all the terminal output here.


:P I did that, and it worked beautifully.  I took "logithèque" out of the bar on the left and put synaptic there instead, problem solved.  Since I didn't get on with logithèque anyway, this seems like a good solution.  Just a side - question: does anyone know the English name for logithèque?  I presume it doesn't have a French name?

---

### Post by RobGoss on 2016-08-28
> **lila said:**
> Yes, that's it, I think you asked the question while I was typing the answer for essentially the same question posed by mook765
I can download the files, but not burn them.

You are using a Linux desktop environment right now correct? and are you able to boot in to the desktop

---

### Post by lila on 2016-08-28
> **RobGoss said:**
> You are using a Linux desktop environment right now correct? and are you able to boot in to the desktop

yes, I'm using a linux desktop environment... what does "booting into the desktop" mean?  Booting up the computer and then it works as normal?  I'm not even sure if I'm having a computer or a language lack of understanding with this question :) ...

I have two computers, one desktop, one laptop, both running with ubuntu-only installs since day 1( bought them pre-installed with ubuntu from a small company in Paris that does essentially only that).  The desktop worked better than the laptop and has our printer installed on it and all that. I use the desktop for my business (absolutely not computer-related).  The laptop is mostly used by other family members to check e-mails and watch movies... less critical.
It's the laptop that has the bug that means I can't burn .iso files.  
My original upgrade which went wrong was on the desktop.  So, I used the old 14.04 DVD I had because I could not burn a 16.04 one once the desktop was unusable with the failed upgrade.  If you want more explanations, try this thread which I posted before this current one:  [https://ubuntuforums.org/showthread.php?t=2335131]("https://ubuntuforums.org/showthread.php?t=2335131")

---

### Post by RobGoss on 2016-08-28
> [COLOR=#000000]yes, I'm using a linux desktop environment... what does "booting into the desktop" mean? Booting up the computer and then it works as normal? I'm not even sure if I'm having a computer or a language lack of understanding with this question [/COLOR]:smile:[COLOR=#000000] ...[/COLOR]

Yes that's what I mean, Ubuntu has a lot of good software programs to allow us to burn ISO files [Startup disk creator]("https://apps.ubuntu.com/cat/applications/precise/usb-creator-gtk/") is one of many and it work great you can install it right from the Software center

---

### Post by oldos2er on 2016-08-28
> **lila said:**
>  does anyone know the English name for logithèque?  I presume it doesn't have a French name?

It's referring to the Software Center.

---

### Post by lila on 2016-08-31
> **oldos2er said:**
> It's referring to the Software Center.

:D thanks!

---


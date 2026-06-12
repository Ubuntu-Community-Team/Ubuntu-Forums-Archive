---
title: "Adobe Acrobat on Feisty Fawn 7.04"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by ADloser on 2007-04-22
I just upgraded to Ubuntu 7.04 and I noticed my Adobe Acrobat Reader is gone and I can't find it in the Add/Remove. I tried 
```
sudo apt-get install acroread 
```
and it returns 
E: Package acroread has no installation candidate

Help! How do I install Adobe Acrobat Reader?
 Thanks!

---

### Post by L0cKd0wN on 2007-04-22
Acroread is not available in the typical feisty repos for licensing reasons. So follow my instructions (again for feisty 7.0.4 only):
[B]
1. Add gpg key:[/B]
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

**2. Edit sources.list with new repo data:**
sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

**3. Apt-get update:**
sudo apt-get update

**4. Install**
sudo apt-get install acroread

There's also many other third party packages in the medibuntu repo, for example w32 codecs, skype, and google earth. I encourage you to look around the Medibuntu web site.

Cheerz! Hope this helps!

~L0cKd0wN

---

### Post by ADloser on 2007-04-22
I installed it but it doesnt open! When I try to open acrobat nothing happens and when I try to open a PDF on a website, firefox just freezes. Help!

---

### Post by ozorba on 2007-04-23
The best way to install Acrobat Reader is via Automatix. It just works!

---

### Post by girlfreddy on 2007-04-23
I just tried this method to install automatix and this is what came up.

helene@ubuntuhome:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
OK
helene@ubuntuhome:~$ sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
--09:26:38--  [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving medibuntu.sos-sts.com... 88.191.13.100, 88.191.26.58, 88.191.30.43, ...
Connecting to medibuntu.sos-sts.com|88.191.13.100|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 240 [text/plain]

100%[====================================>] 240           --.--K/s             

09:26:38 (12.73 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [240/240]

helene@ubuntuhome:~$ sudo apt-get update
E: Type '&#8220;deb' is not known on line 48 in source list /etc/apt/sources.list

What am I doing wrong?

(ps. then I go to synaptic and this appears.

E: Type '&#8220;deb' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.)

---

### Post by compiledkernel on 2007-04-23
output a 

sudo cat /etc/apt/sources.list 

to this thread.

---

### Post by mike2357 on 2007-04-23
I also experienced frustration in trying to get Adobe Acrobat reader to run in Fiesty.

First, I suggest you consider other PDF readers -- Fiesty contains Evince, which I've found to be quite good.  There's also kpdf.  I've never used it.  Since they are part of Ubuntu, I suggest you start with these products.

I downloaded the free Adobe Acrobat Reader product from the Adobe web site, because I need to frequently complete a "fillable Adobe document".  Everything worked fine when I first installed, but later that day after adding some libraries it stopped working.  I have a work-around if you find that neither Evince nor kpdf meet your needs.

I don't mind sharing it but I don't guarantee the results; they may just work on my machine.  I do not think it is fair to call the problem a bug since Adobe doesn't list Ubuntu as one of the GNU/Linux distributions that are supported.

If you interested, let me know by posting back on this thread, and show the output of the following commands:

cd /usr/lib
ls -lLd libgtk-x11*

---

### Post by girlfreddy on 2007-04-24
Here is the output compiledkernel.

helene@ubuntuhome:~$ sudo cat /etc/apt/sources.list 
Password:
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) Feisty main&#8221;
helene@ubuntuhome:~$

Maybe I should also add that there is nothing on my Ubuntu partition that I cannot lose. If I have to do a fresh install I can easily enough. And I didn't know that Automatix wasn't supported by Canonical. Guess I should come here more often. Thanks for your help.

---

### Post by inktomi7 on 2007-04-24
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) Feisty main&#8221;

should become

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) Feisty main

(remove the ")

edit: and maybe change Feisty to lowercase

---

### Post by pestilence4hr on 2007-04-24
For those not comfortable with adding non-official repositories, never fear!  You can still install the edgy acroread package and it will work just fine in feisty.  Here's how:

```
wget http://security.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb
sudo dpkg -i acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb
```

And now you have it.

Should the download link change in the future (perhaps a new security release would do that, I don't know), you can find the .deb by following this link:  [http://packages.ubuntu.com/edgy/text/acroread](http://packages.ubuntu.com/edgy/text/acroread)  and clicking on "i386".

---

### Post by k0rv3n on 2007-04-24
> **pestilence4hr said:**
> For those not comfortable with adding non-official repositories, never fear!  You can still install the edgy acroread package and it will work just fine in feisty.  Here's how:

```
wget http://security.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb
sudo dpkg -i acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb
```

And now you have it.

Should the download link change in the future (perhaps a new security release would do that, I don't know), you can find the .deb by following this link:  [http://packages.ubuntu.com/edgy/text/acroread](http://packages.ubuntu.com/edgy/text/acroread)  and clicking on "i386".

Will this get the mozilla plugin to?

EDIT: This works if you download those packages separatley

---

### Post by girlfreddy on 2007-04-25
> **inktomi7 said:**
> &#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) Feisty main&#8221;

should become

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) Feisty main

(remove the ")

edit: and maybe change Feisty to lowercase

Unfortunately, I don't know how to change this. I also can't get into my synaptic any longer as something there has changed.

edit: searched the forums, found out how to fix synaptic and it's done. I've also wiped automatix off the sources list as it was just causing problems. I'll try some of the other solutions to getting Adobe Acrobat. Thanks to everyone for helping.

---

### Post by arkangel on 2007-04-25
maybe is relevant  if using 64 bit 

[http://www.mjmwired.net/resources/mjm-fedora-fc6.html#acrobat](http://www.mjmwired.net/resources/mjm-fedora-fc6.html#acrobat)

---

### Post by rgrig on 2007-04-25
> **mike2357 said:**
> First, I suggest you consider other PDF readers -- Fiesty contains Evince, which I've found to be quite good.  There's also kpdf.  I've never used it.  Since they are part of Ubuntu, I suggest you start with these products.

The fonts in those readers look awful compared to acroread. I think the best solution is to download the debian package (for edgy) and install it.

---

### Post by girlfreddy on 2007-04-25
I have 32 bit so the original should have worked. I can download a PDF and read it but the problem is in a site I go to get some of my bills. The site checks for Adobe Reader and won't let me see my bills without it. And I can't seem to get the reader to work.

---

### Post by shouravv on 2007-04-25
This is the easiest and safest way of solving the issue:

1. Add this line at the end of sources.list - 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe

2. Next, add these packages - acroread, acroread-escript, acroread-plugins, and mozilla-acroread - using synaptic package manager or aptitude or apt-get.

(You may use nano to edit sources.list. Type

nano /etc/apt/sources.list

Add the line mentioned line anywhere in this file, and save it).

---

### Post by girlfreddy on 2007-04-26
Thanks shouravv. Worked like a charm. Yea, I can pay my bills ;)

---

### Post by mannheim on 2007-04-26
> **rgrig said:**
> The fonts in those readers look awful compared to acroread

I found that to be true using evince ("Document Viewer") in edgy and earlier. But in feisty, the fonts in evince have improved a lot (at least for the documents/fonts that I usually look at). For me, acroread is still a must-have for the extra features it brings; but for speed and readability, I think evince is now pretty good.

---

### Post by titus1950 on 2007-04-26
> **pestilence4hr said:**
> For those not comfortable with adding non-official repositories, never fear!  You can still install the edgy acroread package and it will work just fine in feisty.  Here's how:

```
wget http://security.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb
sudo dpkg -i acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb
```

And now you have it.

Should the download link change in the future (perhaps a new security release would do that, I don't know), you can find the .deb by following this link:  [http://packages.ubuntu.com/edgy/text/acroread](http://packages.ubuntu.com/edgy/text/acroread)  and clicking on "i386".

Thank you....
Plugins for firefox are there. 
Works,great.

---

### Post by fakie_flip on 2007-04-29
> **shouravv said:**
> This is the easiest and safest way of solving the issue:

1. Add this line at the end of sources.list - 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe

2. Next, add these packages - acroread, acroread-escript, acroread-plugins, and mozilla-acroread - using synaptic package manager or aptitude or apt-get.

(You may use nano to edit sources.list. Type

nano /etc/apt/sources.list

Add the line mentioned line anywhere in this file, and save it).

That repo is for Edgy. In the instructions it says edgy-security, but I am using Feisty Fawn. What should I do?

---

### Post by S29K on 2007-04-30
Adobe Acrobat Reader is not available in the Feisty Fawn repositories so any Feisty users must add the Edgy repository to their sources.list to make it available.  Synaptic will default to the Feisty distribution for any packages found in both the Edgy and Feisty repositories so you needn't worry about messing up anything that you have installed in Feisty.

---

### Post by findik1 on 2007-05-15
use Automatix

---


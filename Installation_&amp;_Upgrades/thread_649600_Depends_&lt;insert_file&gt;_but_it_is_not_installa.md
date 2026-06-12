---
title: "Depends: &lt;insert file&gt; but it is not installable"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by BTetlow on 2007-12-25
Hello and Help....

I installed Ubuntu 7.10 on my laptop a few weeks back and am happy to finally (12 years experimenting) to have a Linux Distro that meets my needs. Everything worked fine out of the box on my laptop...no tinkering required.

So impressed I installed it on my home PC....but things haven't gone so well.

The install worked fine, but I seem to be unable to add any of the apps that I added on my laptop.

1. Scribus (in Add/Remove) tells me "Scribus cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."    but it installed fine on my Laptop. Not to worry I can run the Windows version via WINE.

2. I went to install Exaile
When I try via Add/Remove

[FONT="Courier New"]Cannot install 'exaile'
This application conflicts with other installed software. To install 'exaile' the conflicting software must be removed first.
Switch to the 'synaptic' package manager to resolve this[/FONT] conflict.


So when I try via Synaptic I get

[FONT="Courier New"]exaile:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
 Depends: python-pysqlite2  but it is not installable
 Depends: python-pyvorbis  but it is not installable
 Depends: python-mutagen  but it is not installable[/FONT]



3. So I went and tried to install the Gstreamer extras

Tried via ADD/REMOVE
[FONT="Courier New"]
Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/FONT]

So when I try via Synaptic I get

[FONT="Courier New"]gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable[/FONT]

and this sort of error continues which makes me think something has gobe very wrong. All these apps installed and worked fine on my Laptop, but's it's almost as thought there is something about the architecture of my home machine that it doesn't like.

The home machine is a pretty regular machine. AMD Dual Core 3800 running 2Gig of RAM. I really want UBUNTU to work for me but I just don't know enough (nor can find enough) to tell me what to do next.

HELP?   PLEASE?

---

### Post by seshomaru samma on 2007-12-25
I would suspect that there is something wrong with the sources list ,perhaps they do not match your install version, though I don't know why that would occur .
Can you post your sources list?
```
cat /etc/apt/sources.list
```
and also whats the output of
```
sudo lsb_release -a
```

did you try to install anything else? 
did it work?

---

### Post by BTetlow on 2007-12-25
Seshumaru,

Thanks for your reply.

First, yes I have manged to install some software (Thunderbird). Though even when I tried to install the Development version of Scribus, I got a similar set of errors.

Anyway, I have done as you asked and run those commands, the output (minus comments) is below

[B]bradford@ZEN:~$ cat /etc/apt/sources.list
[/B]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


and then the other command

**bradford@ZEN:~$ sudo lsb_release -a**
[sudo] password for bradford:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

Thanks again and really looking forward to your response.

Bradford

---

### Post by robfuller on 2007-12-25
Bradford,

I am complete newcomer to Ubuntu & Linux (since earlier today!), so I don't know anything about technicalities. But just in case it helps..... I was getting exactly the same error messages as you when trying to install the Gstreamer plugins on a freshly-installed copy of Ubuntu 7.10 - but running the "system update" process appeared to fix it. (The system update icon had appeared on the top right of my screen, near the clock. It takes quite some time to run.) After that, I was able to install the Gstreamer plugins straight away with no problems.

Rob

---

### Post by BTetlow on 2007-12-25
Rob.

Thanks for that. I thought that might be the case to, especially as when I installed 7.10 I had hit my monthly download limit and my ISP ad scaled me bac to 56K (yes...we are still that primitive in Australia). I thought maybe the slow speed had upset Ubunutu.

I re ran the Update utility and things got more complicated. It did install some updates but this time the updater refused to install two packages (compiz and lib_popler) and so they now sit in my update application as uninstallable applications.

I just can't believe that the laptop install went SOOOOO smoothly and yet the standard desktop machine is giving me grief.

I so want to use Linux.....but the hurdles.......

---

### Post by Partyboi2 on 2007-12-25
> **BTetlow said:**
> Seshumaru,

Thanks for your reply.

First, yes I have manged to install some software (Thunderbird). Though even when I tried to install the Development version of Scribus, I got a similar set of errors.

Anyway, I have done as you asked and run those commands, the output (minus comments) is below

[B]bradford@ZEN:~$ cat /etc/apt/sources.list
[/B]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


and then the other command

**bradford@ZEN:~$ sudo lsb_release -a**
[sudo] password for bradford:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

Thanks again and really looking forward to your response.

Bradford
When you say  "the output (minus comments) is below" do you mean you removed the # from in front of them?

---

### Post by BTetlow on 2007-12-25
Sorry, no...what I meant was that I removed every line that had a # in front of it and only posted the lines without the #....here it is in its entirety.

Which in retrospect is probably what I should have posted :-)

[B]bradford@ZEN:~$ cat /etc/apt/sources.list
[/B]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by oldos2er on 2007-12-26
Open up your sources.list as root: type "gksudo gedit /etc/apt/sources.list" in a terminal. Remove the comment marks from each deb and deb-src line that has them. Save and exit the file, then in the terminal type "sudo aptitude update && sudo aptitude upgrade". Hopefully after this you can install Exaile and the other programs you want.

---

### Post by BTetlow on 2007-12-26
I'm glad you have advised that. I was very tempted o do that but I didn't want to make things worse. I shall try it shortly and see what happens.

I've also had one of "those" moments as I realised I updated my motherboard last year and I never checked but I assumed that the new Athlon was 32bit...and have just realised that it isn't. Maybe I should be using the AMD 64bit install instead???

---

### Post by BTetlow on 2007-12-26
Ann,

Well thanks again. It seems to have done something and it looks positive, however it is telling me it needs to download and install 128MB of stuff. As I mentioned in my previous post I am currently bandwidth limited to 56K so that will take forever. The bandwidth limit is lifted at 1am tomorrow morning so I'll proceed then.

Do you think the reason that it flagged (or commented out) those repos was because it gave up trying to verify at my low connection rate? Otherwise why else would it fail to verify the sources?

Thank you all for your help. I'll post an update tomorrow about what happened, and I guess I will have to think about installing the 64 bit version instead. But I'll wait until its fixed before I try and break it again :-)

Bradford

---

### Post by Partyboi2 on 2007-12-26
> **BTetlow said:**
> Ann,

Well thanks again. It seems to have done something and it looks positive, however it is telling me it needs to download and install 128MB of stuff. As I mentioned in my previous post I am currently bandwidth limited to 56K so that will take forever. The bandwidth limit is lifted at 1am tomorrow morning so I'll proceed then.

Do you think the reason that it flagged (or commented out) those repos was because it gave up trying to verify at my low connection rate? Otherwise why else would it fail to verify the sources?

Thank you all for your help. I'll post an update tomorrow about what happened, and I guess I will have to think about installing the 64 bit version instead. But I'll wait until its fixed before I try and break it again :-)

Bradford
using the 32bit might slow your system down alittle. If you are thinking of changing to 64bit install, I wouldn't bother with the 128mb updates. Because when you reinstall you will lose those updates

---

### Post by oldos2er on 2007-12-26
There seems to be a bug (or feature, if you prefer) in Gutsy where it will comment out some or all software sources if it can't find a "good" network connection when first installed. If you're getting a high speed connection tomorrow, it should be fine then.

 I think using either the 32- or 64-bit version is personal preference.

---

### Post by BTetlow on 2007-12-26
Well the update did its thing and installed lots of stuff, but even after a reboot I am getting exactly the same errors as before.

The sources.list looks like it should now with no sources commented out.

Where to now oh wise people of Ubuntu land?

---

### Post by Partyboi2 on 2007-12-27
> **BTetlow said:**
> 
Tried via ADD/REMOVE
[FONT=Courier New]
Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/FONT]

So when I try via Synaptic I get

[FONT=Courier New]gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable[/FONT]

I was reading up on this and someone found that cleaning out  /var/lib/apt/lists/partial/ worked for them.
To try this:
Open up  /var/lib/apt/lists/partial/ and remove all the files you see there, then run
```
sudo apt-get update
```[http://ubuntuforums.org/showthread.php?t=532613](http://ubuntuforums.org/showthread.php?t=532613)

---

### Post by BTetlow on 2007-12-27
Thanks partyboi....That particular directory was empty, even when I chose show hidden files.

I ran the command anyway..but sorry, no joy.

---

### Post by Partyboi2 on 2007-12-27
What happens if you try the apt-get fix command
```
sudo apt-get install -f
```

---

### Post by BTetlow on 2007-12-27
Partyboi,

This is what it says

**bradford@ZEN:~$ sudo apt-get install -f**

[sudo] password for bradford:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks for walking me through this.....

---

### Post by BTetlow on 2007-12-28
Okay,

Well this is getting no where fast. I suspect that something has gone wrong with the installation. Possibly due to the fact that my ISP had cut me back to 56K and perhaps this caused some problems.

So I might just better off cutting my losses and blowing Ubuntu away and starting again. From experience I know that if I kill the ubuntu partion (when I have XP loaded) this will screw up GRUB and I won't be able to boot XP, so......

If I....

1. Load up XP
2. Destroy the Ubuntu partions
3. Reboot my machine withe the LIVECD loaded
4. Reinstall Ubuntu

Will this make everything ok with GRUB? Does anyone think this will actually help?

Bradford

---

### Post by Partyboi2 on 2007-12-28
You should be able to boot the live cd, choose to install and when you get to the partition part choose to install over the current one.
Hopefully the next one will work :)

---

### Post by BTetlow on 2007-12-28
I'll try it tonight (I still have some high bandwidth available in off peak period) and see how it goes.

Stay tuned!

---

### Post by BTetlow on 2007-12-29
Well alas the reinstall didn't change a thing. I still can't install most of the software I want and am getting pretty much the same errors.

Thanks for your help everyone....back to Windows for me. 

Maybe the next Ubuntu release will work? Well I'll try again in another 6 months.

Regards

Bradford

---

### Post by hwertz on 2007-12-31
OK, so I know you already went back to Windows.. but for reference, I just had the same problem. (libmad0 and libidtag0 not found.)   I don't know what went wrong, but to fix it I went to the System->Administration->Software Sources (the same screen as if you chose Settings->Repositories from in Synaptic).  I changed the "Download from" from "Server for United States" (I suppose maybe for you it'd be "Server for Australia?") to "Main Server".  I told Synaptic to reload.  I didn't have to leave this changed permanently --I changed it back to "Server for US" right after that and reloaded and the libmad0 etc. were still all there.  Weird.

     I don't know if my package list download got cut off, or if it was temporarily corrupted on some mirror or two, or what -- but whatever, that fixed it for me.

Rock on! :guitar:

---

### Post by BTetlow on 2008-01-01
HWERTZ,

I'll give it a go when I get home. I left Ubuntu on my machine, just hidden away. After the amount of grief Windows gave me this morning I'm willing to keep plugging away.

It seems to be ANY software (apart for some reason Thunderbird) that won't install and is constantly telling me their are conflicts.

Will let you know how things go.

B.

---

### Post by BTetlow on 2008-01-02
Okay, well I agree with you. 

WEIRD!!!!

I'll admit I was very skeptical about your solution. But it worked

Yep, did what you said and everything is now installing just as it did with my laptop.

Thank you a billion times! I can't think why the files in one server would be different to another...but there you go!

---


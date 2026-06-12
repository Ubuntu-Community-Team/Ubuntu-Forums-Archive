---
title: "Installing Firefox 26 on Hardy Heron"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by Rutherford_Hayes on 2014-01-26
My mother was complaining of threats by Youtube and Facebook to stop supporting her current version of Firefox so I tried to install the new version: I first downloaded the file firefox-26.0.tar.bz2 then I deleted the existing form of Firefox. I tried to look up tutorials, on my laptop, to install the new version with the terminal but no command on any tutorial yielded anything but an error message, command not found, no existing directory, all that jazz. Then I decided to install another browser in the hope that it would be capable of updating itself as Firefox was not, I was unsuccessful in this endeavor seemlingly because the Add/Remove Applications thing seems to require the internet, and, having deleted Firefox, it was unable to reach the internet.

I guess I don't actually need Firefox 26, I just need some web browser that can be installed on Hardy Heron and can get updates and the updated flash player so it can continue to play videos and games on Facebook. I am fairly inept at this stuff so I request that any explanations of how I should go about achieving this goal be phrased very simply so I don't mess it up.

Thank you for the help in advance.

---

### Post by monkeybrain20122 on 2014-01-26
Huh??? Hardy H What?? What year is this?? Please make a flash install of a supported version of Ubuntu.

---

### Post by vasa1 on 2014-01-26
Whichever browser you consider, check its minimum requirements. Some browsers insist on a minimum version number for the operating system because the additional software the browser needs may not be present (and possibly cannot be installed) on older operating systems.

---

### Post by Rutherford_Hayes on 2014-01-26
The computer is 11 years old, it couldn't really handle an upgrade I don't think. Can I not make it work with Hardy?

---

### Post by monkeybrain20122 on 2014-01-26
You should try lubuntu 13.10 or xubuntu 12.04 LTS.  BTW, Fifefox doesn't need install. Just extract and click "firefox" (or firefox-bin) but it may require some up to date system libraries.

---

### Post by Rutherford_Hayes on 2014-01-26
And will upgrading get me those up-to-date system libraries?

---

### Post by monkeybrain20122 on 2014-01-26
Yes. Don't "upgrade". Backup your data and do a fresh install, with HH so far away I gurantee that upgrade will not work. And updated firefox is in the repository, no need to download from Mozilla.

---

### Post by Rutherford_Hayes on 2014-01-26
Thank you, anything I should know about the fresh install?

---

### Post by carl4926 on 2014-01-26
Probably, no.... certainly your cpu will not work with the latest flash that come in the newer *buntu version
Which means you will have some work getting the old flash in place
IIRC the Ubuntu derivative Mint, version 13 has made the older flash player available in it's repos

---

### Post by monkeybrain20122 on 2014-01-26
> **carl4926 said:**
> Probably, no.... certainly your cpu will not work with the latest flash that come in the newer *buntu version
Which means you will have some work getting the old flash in place
IIRC the Ubuntu derivative Mint, version 13 has made the older flash player available in it's repos

The 'latsest' flash from Ubuntu's repo is still 11.2 I think it will work. Old flash should be avoided because it is a security risk.

@OP Install the greasemonkey script Viewtube for Firefox and install gecko-mediaplayer. That way you don't need flash for some of the popular sites (Vimeo, Youtube, Dailymotion and a few others). With a machine that old even if flash works it is a drain on the system. [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

To do a fresh install, download an iso and make a bootable live CD or usb (if your machine supports booting from usb), then boot up and install on the whole disk. It is quite easy as you don't have multibooting or other strange layouts.

You may also try lxle [http://lxle.net/](http://lxle.net/)
There are some pros and cons IMHO I stated here [http://ubuntuforums.org/showthread.php?t=2125764&page=18](http://ubuntuforums.org/showthread.php?t=2125764&page=18)

---

### Post by carl4926 on 2014-01-26
> The 'latsest' flash from Ubuntu's repo is still 11.2 I think it will  work. No very unlikely with the cpu the OP likely has, it needs at least sse2


> Old flash should be avoided because it is a security risk.I agree, but if he upgrades it may be the only option

---

### Post by slooksterpsv on 2014-01-26
What are the specs of the computer?

---

### Post by Rutherford_Hayes on 2014-01-26
So I burn a disc and put it in and it installs?

---

### Post by Rutherford_Hayes on 2014-01-26
> **slooksterpsv said:**
> What are the specs of the computer?

I'm not sure 20GB harddrive, 200MB RAM or something.

---

### Post by carl4926 on 2014-01-26
> **Rutherford_Hayes said:**
> So I burn a disc and put it in and it installs?

Not exactly
It requires user input

---

### Post by carl4926 on 2014-01-26
> **Rutherford_Hayes said:**
> I'm not sure 20GB harddrive, 200MB RAM or something.

256MB maybe
Anyway, that's low
You will want to skip the live session and head right to install
And Lubuntu is what you want

---

### Post by Rutherford_Hayes on 2014-01-26
> **carl4926 said:**
> Not exactly
It requires user input

I've burned a disc, got it in the tray, and have the file browser open looking at the disc's contents; how do I go about the installation?

---

### Post by Dennis N on 2014-01-26
You need to step back and get an overview of the process. Take out the cd and spend a few minutes reading the installation guide:

[http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

The guide applies to all of the *buntus: ubuntu, lubuntu, xubuntu, ....

[901]

---

### Post by Rutherford_Hayes on 2014-01-26
I told it to install Lubuntu and it seemed to begin, showing a blue screen with the word Lubuntu and four dots, then I saw the logo again and the screen has been black ever since.

---

### Post by Dennis N on 2014-01-26
Your guess on the system ram (200mb) in post #14 has to be way too low. I just started up Ubuntu 8.04 + Firefox to see and it is using 450 mB.

I suggest you back out of the install and try the live mode first. That way you can test if everything works. As long as you haven't seen any of the screens pictured in the guide, your old system is still intact.

[902]

---

### Post by Rutherford_Hayes on 2014-01-26
I checked the disc for problems at the beginning by the way.

The screen is still black. Going by the directions [here]("http://www.ubuntu.com/download/desktop/install-desktop-latest"), it seems I failed immediately after the first step as no such window as the one appearing in the second ever appeared. The computer hummed pretending to be working on the installation I requested then went silent, then the screen went black and the after a little while the computer begin humming again, threatening to actually install, finally the computer went silent again and the screen remained black. That is the present state of the computer.

---

### Post by Rutherford_Hayes on 2014-01-26
> **Dennis N said:**
> Your guess on the system ram (200mb) in post #14 has to be way too low. I just started up Ubuntu 8.04 + Firefox to see and it is using 450 mB.

I suggest you back out of the install and try the live mode first. That way you can test if everything works. As long as you haven't seen any of the screens pictured in the guide, your old system is still intact.

[902]

How would I back out, by restarting?

---

### Post by Dennis N on 2014-01-26
Certainly restart would work, and let it boot to the hard disk.

---

### Post by Rutherford_Hayes on 2014-01-26
> **Dennis N said:**
> Certainly restart would work, and let it boot to the hard disk.

I tried to restart and for a moment saw this nice blue background that looked like Lubuntu before that disappeared and the screen turned white with thin vertical black bars, the disc was also ejected.

---

### Post by Dennis N on 2014-01-26
Notice in Step 5, it says: "The installation process will begin when you click the Install Now button." So if you even got that far, you can abort the whole thing without any damage.

[904]

---

### Post by Rutherford_Hayes on 2014-01-26
Well my screen is stuck on the black and white thing, it does not seem to respond to restart requests.

---

### Post by Dennis N on 2014-01-26
1. Ctrl + Alt + Del
2. Hold down (Alt + PrintScreen) and in sequence, press R, E, I, S, U, B
3. Hold down power button for 5- 10 sec until machine shuts off.

1 or 2 may (or may not) work to reboot, 3 will power off.

[905]

---

### Post by Rutherford_Hayes on 2014-01-26
I went through all the steps of [this guide]("http://www.ubuntu.com/download/desktop/install-desktop-latest"), but, upon restarting the computer it once again froze, this time at a screen where the lower 1/4 is black and where the upper 3/4 is blue with 4 distorted and stretched rightwards Lubuntu logos, below each logo 4 dots. I restarted and faced the same issue.

---

### Post by Rutherford_Hayes on 2014-01-26
I'm still stuck at the screen described above; I previously got a very similar screen on Hardy before the login page opened.

---

### Post by Rutherford_Hayes on 2014-01-26
Please guys, I have absolutely no idea what to do now.

---

### Post by SuperFreak on 2014-01-26
I had similar problems installing Lubuntu on an old laptop (black screen on startup, didn't respond to any key presses); I think it may have been a problem with the graphics card.> Eventually I gave up on it and installed Ubuntu 10.04 but the computer isn't connected to the internet so the fact that it was out dated didn't matter. You may find some help here though[http://www.howtogeek.com/172987/revive-your-old-pc-the-3-best-linux-systems-for-old-computers/]("http://www.howtogeek.com/172987/revive-your-old-pc-the-3-best-linux-systems-for-old-computers/")

---

### Post by slooksterpsv on 2014-01-26
antiX may be a better suited distro for you; I've used it before and it does support flash. It is part of the Mepis Linux distro which is based on Debian, so a lot of the apt-get commands should work. antiX can be run on a computer with as little as 128MB of RAM (I've done it, yeah) albeit not the fastest, it still works.

---


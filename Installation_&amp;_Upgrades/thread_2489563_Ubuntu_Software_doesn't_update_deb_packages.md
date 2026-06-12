---
title: "Ubuntu Software doesn't update deb packages"
date: 2023-08-03
forum: Installation &amp; Upgrades
---

### Post by smart-mart on 2023-08-03
VSCode keeps informing me there are updates available.
I download the deb file but then Ubuntu software does not provide any options to install the update.

only to uninstall.

I believe this to be a bug or missing feature from Ubuntu Software

---

### Post by TheFu on 2023-08-03
> **smart-mart said:**
> VSCode keeps informing me there are updates available.
I download the deb file but then Ubuntu software does not provide any options to install the update.

only to uninstall.

I believe this to be a bug or missing feature from Ubuntu Software

No, working as designed.  

If the software isn't installed using a PPA or Repo, then there's no way for APT to know where to get updates.  If YOU choose to install a .deb file directly, YOU have taken the task of keeping it updated yourself.  The solution is to only use software from reputable repos and PPAs.  The same applies of you install other stuff using any other packaging method that doesn't have a repo.  Examples are source tgz files, python/perl/ruby/go/nodejs modules, appImages, Flatpaks ... and some snaps that aren't maintained.

Some .deb installation scripts, created by the specific .deb package maintainer, will automatically add a PPA during installation, but most do not.  You can try opening a bug with the packager, but I have doubts that will get anywhere.  It is working as designed.

---

### Post by #&amp;thj^% on 2023-08-03
> **smart-mart said:**
> VSCode keeps informing me there are updates available.
I download the deb file but then Ubuntu software does not provide any options to install the update.

only to uninstall.

I believe this to be a bug or missing feature from Ubuntu Software

TheFu explains your findings, and why.
Maybe this will help you, The following commands work for me:
```

wget 'https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64' -O /tmp/code_latest_amd64.deb
sudo dpkg -i /tmp/code_latest_amd64.deb
```

Place those two commands into an executable Bash script called auto-update-vscode, and you can simply run that from your shell any time Visual Studio Code says it's out of date.
Make sure you uninstall your first one, or you will end up Two versions of VSCode
```
apt policy code 
code:
  Installed: 1.80.2-1690491597
  Candidate: 1.80.2-1690491597
  Version table:
 *** 1.80.2-1690491597 100
        100 /var/lib/dpkg/status

```
Now:
```
code --version
1.80.2
2ccd690cbff1569e4a83d7c43d45101f817401dc
x64

```

---

### Post by #&amp;thj^% on 2023-08-03
I just talked with nice folks over at VScode, and they tell me it is as easy as:
```
sudo apt install code
```
To update.
To test them i ran it, and now at:
```
apt policy code 
code:
  Installed: 1.81.0-1690980880
  Candidate: 1.81.0-1690980880
  Version table:
 *** 1.81.0-1690980880 500
        500 http://packages.microsoft.com/repos/code stable/main amd64 Packages
        100 /var/lib/dpkg/status

```
It has to be ran as i have showed, and not "apt-get install code"
Hope that helps.

---

### Post by TheFu on 2023-08-03
Leave it to MSFT to name something so generically as to be completely non-descriptive.

Windows, Bob, Code ... off the top of my head.

---

### Post by smart-mart on 2023-08-07
I still think its poorly designed.
I have already downloaded the deb file.

surely me double clicking on it is me showing interest to either install or update the package.


Why make me jump into the command line?

---

### Post by TheFu on 2023-08-07
> **smart-mart said:**
> I still think its poorly designed.
I have already downloaded the deb file.

surely me double clicking on it is me showing interest to either install or update the package.


Why make me jump into the command line?

And what if your system isn't on the internet, behind an air-gapped network?  Then you'd have massive problems as updates try and fail to run.  There is a method to the madness.  Step back and consider there are millions of other users of Debian packages.  The APT layer tries to solve those needs like you have, but that is over the stand-alone layer provided by .deb files.  This is an elegant design, following the _Unix Philosophy_. [https://en.wikipedia.org/wiki/Unix_Philosophy](https://en.wikipedia.org/wiki/Unix_Philosophy)  It is different than what MSFT or MacOS do, by design.

You are free to think it is poorly designed.  I used to be like that with many Unix solutions about 30 yrs ago, then it became clearer and clearer that the people who came before really were very, very, smart.  There is a method.

---

### Post by MAFoElffen on 2023-08-10
In posts #3 and #4, those members hinted everything was working as designed... But (rather) as per how "you" had installed VSCode, which you only glossed over. No one has control over how you do that or where from. That opens up a lot of variables.

I have a question for the OP... The questions not asked was how did you originally install VSCode and where from? The next question would have been do you have their repo's in your sources.d?
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep -e 'repos/vscode' -e '/repos/code' /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/vs-code.list:deb [arch=amd64] http://packages.microsoft.com/repos/vscode stable main
/etc/apt/sources.list.d/vscode.list:deb [arch=amd64,arm64,armhf] http://packages.microsoft.com/repos/code stable main
/etc/apt/sources.list.d/vs-code.list.save:deb [arch=amd64] http://packages.microsoft.com/repos/vscode stable main
/etc/apt/sources.list.d/vscode.list.save:deb [arch=amd64,arm64,armhf] http://packages.microsoft.com/repos/code stable main

```
I have those. I don't need an additional scripts to do my updates. I'm just wondering where there differences were on installation.

---

### Post by TheFu on 2023-08-10
> **smart-mart said:**
> I still think its poorly designed.
I have already downloaded the deb file.

surely me double clicking on it is me showing interest to either install or update the package.


Why make me jump into the command line?

Do you understand what a PPA is?  Do you understand what they are used for and how they extend the system to allow non-core repos to be used?

Don't be fixated on 1 specific use-case that applies to only you.  If you do that, you end up with forced and failing upgrades when you don't want any.  Linux is about control, flexibility. If there is a PPA, which there appears to be, then you can have it work the way you desire as 1fallen posted above. Let your intent known.  BTW, you can add a PPA inside a GUI if you like, but it is harder to show here.  

Why would we bother with 3 screen captures when running 2 commands is simple and works?

In some ways, MS-Windows is easier.  In 1000 other ways, it is lacking, which is why we run Linux.

---


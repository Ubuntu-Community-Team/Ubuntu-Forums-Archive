---
title: "System / Software Update fails (message included)"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by bertrand.barbier on 2011-02-27
I am looking for help. I am as newbie as they come, new to Ubuntu and I'm loving it very much. I've ended up removing Windows.

I've encountered my first problem which I cannot seem to solve, and besides backing up everything and re installing Ubuntu 10.10 I thought I'd post a message.

Here's the deal, I cannot update my system. The message below is displayed after I try updating it through the terminal. I've copied and pasted the last bit that is displayed in the terminal.

I would appreciate any help I can get. Since re installing Ubuntu and finding every single program I have is a hassle and costly (I don't have unlimited broadband connection)

Thanks in advanced

**In case some people do not feel safe opening the .txt file**

Message that displays upon update failure:


Hit [http://www.mirror.upm.edu.my](http://www.mirror.upm.edu.my) maverick-security/universe i386 Packages     
Fetched 23.1kB in 21s (1,093B/s)                                              
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release) 

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release](http://archive.canonical.com/ubuntu/dists/maverick/Release) 

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release](http://packages.medibuntu.org/dists/maverick/Release) 

W: Some index files failed to download, they have been ignored, or old ones used instead.
bertrand@bertrand:~$

---

### Post by thefasterblueone on 2011-02-27
Run this in terminal:

```
sudo apt-get update
```

let us know if you get any errors.

---

### Post by Old_Grey_Wolf on 2011-02-27
Try entering these commands in a terminal.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

```

---

### Post by bertrand.barbier on 2011-02-27
> **thefasterblueone said:**
> Run this in terminal:

```
sudo apt-get update
```

let us know if you get any errors.
Hi there,

I got the message trying this out.

Thanks, I'll see if a second time it does anything.

---

### Post by bertrand.barbier on 2011-02-27
> **Old_Gray_Wolf said:**
> Try entering these commands in a terminal.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

```
Hi,

I've tried following the lines. However, I get told access denied. I tried something on the top of my head and inserted the sudo command in front. It asked me for the password and I put it then it displayed this:

bertrand@bertrand:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
bertrand@bertrand:~$ cd /var/lib/apt
bertrand@bertrand:/var/lib/apt$ 
bertrand@bertrand:/var/lib/apt$ mv lists lists.old
mv: cannot move `lists' to `lists.old': Permission denied
bertrand@bertrand:/var/lib/apt$ mv lists lists.old
mv: cannot move `lists' to `lists.old': Permission denied
bertrand@bertrand:/var/lib/apt$ 
bertrand@bertrand:/var/lib/apt$ sudo mv lists lists.old
[sudo] password for bertrand: 
bertrand@bertrand:/var/lib/apt$ mv lists lists.old
mv: cannot stat `lists': No such file or directory
bertrand@bertrand:/var/lib/apt$ cd~
No command 'cd~' found, did you mean:
 Command 'cda' from package 'xmcd' (universe)
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cdp' from package 'irpas' (multiverse)
 Command 'cd5' from package 'cd5' (universe)
cd~: command not found
bertrand@bertrand:/var/lib/apt$ cd ~
bertrand@bertrand:~$ sudo apt-get clean
bertrand@bertrand:~$ sudo cd /var/lib/apt
sudo: cd: command not found
bertrand@bertrand:~$ cd /var/lib/apt
bertrand@bertrand:/var/lib/apt$ sudo mv lists lists.old
mv: cannot stat `lists': No such file or directory
bertrand@bertrand:/var/lib/apt$ sudo mv lists lists.old
mv: cannot stat `lists': No such file or directory
bertrand@bertrand:/var/lib/apt$ 

As mentioned before, I'm as noob as it gets.

---

### Post by thefasterblueone on 2011-02-27
Be sure you don't have any oyher updating applications open, like Synaptic Package Manager, or Ubuntu Software Center.

Try this in terminal:

```
sudo dpkg --configure -a
```

---

### Post by Old_Grey_Wolf on 2011-02-27
> **bertrand.barbier said:**
> Hi,

I've tried following the lines. However, I get told access denied. I tried something on the top of my head and inserted the sudo command in front. It asked me for the password and I put it then it displayed this:
...

OK, the lines need sudo except for cd
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

You already entered some of them with sudo so you may have already moved list to list.old. It will give you an error that list does not exist.

---

### Post by bertrand.barbier on 2011-02-27
I've tried this. I don't see anything noticeable happening. I will try updating my system and see if I get the errors.

---

### Post by bertrand.barbier on 2011-02-27
> **thefasterblueone said:**
> Be sure you don't have any oyher updating applications open, like Synaptic Package Manager, or Ubuntu Software Center.

Try this in terminal:

```
sudo dpkg --configure -a
```

Hi again,

I hope you get the pictures and they are legible. I've tried doing this. It does not look like much happened but the update icon appeared in my notification area so that I could click on it to update it.

When I did, the two messages (included in the pictues) popped up.

---

### Post by thefasterblueone on 2011-02-27
Ok. Be sure you don't have any open Applications, reboot if you have to then run this command :

```
sudo rm /var/lib/dpkg/lock
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by bertrand.barbier on 2011-02-27
> **Old_Gray_Wolf said:**
> OK, the lines need sudo except for cd
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

You already entered some of them with sudo so you may have already moved list to list.old. It will give you an error that list does not exist.
Hi again,

Wow! Words fail to describe how glad I am to see progress! It worked in the terminal, now I've opened the Update Manager and things are going according to the norm. So far so good, but I don't want to count my chickens before they hatch.

I posted the comment with pictures before I got your this message. I'll let you know once the 34MB of updates are done. Many thanks for your support!

---

### Post by bertrand.barbier on 2011-02-27
Many many thanks to Old_Gray_Wolf and thefasterblueone!!!

You both have been very helpful and supported me with this. I can finally use the update manager as I used to.

Using the codes to input in the terminal by Old_Gray_Wolf, the problem resolved.

Should I somehow mark this thread as solved??

Bless you both!

Cheers!

:D

---

### Post by bertrand.barbier on 2011-02-27
> **Old_Gray_Wolf said:**
> OK, the lines need sudo except for cd
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

You already entered some of them with sudo so you may have already moved list to list.old. It will give you an error that list does not exist.
yeah I did get the message 'doesn't exist'.

---

### Post by Old_Grey_Wolf on 2011-02-27
> **bertrand.barbier said:**
> 
Should I somehow mark this thread as solved??


If it is solved.

At the top of the thread, use Thread Tools -> Mark this thread as solved.

Edit: When I refreshed the thread, I saw that you had already make it as solved.

---

### Post by Old_Grey_Wolf on 2011-02-27
> **bertrand.barbier said:**
> I posted the comment with pictures before I got your this message. I'll let you know once the 34MB of updates are done. Many thanks for your support!

I can't resist laughing at this. Look at what is in the background of your screenshots.

:lolflag:

---

### Post by bertrand.barbier on 2011-02-28
Hi there,

I checked.. You mean 'beans=fart' line? that's a funny line, along with your reply... :)

I was doing stuff on the fly, so to speak..

---

### Post by woodmaster on 2011-02-28
> sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
This also solved my upgrade issues.  My errors weren't quite the same, but software center thought I had an incomplete upgrade(probably due to me not removing PPA's prior to upgrading.)  Only thing is my sound doesn't work properly.  It plays too fast.  But everything else updated fine now! :-)

---

### Post by Old_Grey_Wolf on 2011-02-28
> **woodmaster said:**
> This also solved my upgrade issues.  My errors weren't quite the same, but software center thought I had an incomplete upgrade(probably due to me not removing PPA's prior to upgrading.)  Only thing is my sound doesn't work properly.  It plays too fast.  But everything else updated fine now! :-)

Thank you. It is nice to know that a post has helped someone.

---

### Post by woodmaster on 2011-02-28
yep, we need a thanks button like precentral.net has.

---

### Post by bertrand.barbier on 2011-03-02
Like the saying goes, ' a small prayer goes a long way'. In this case, your thread saved me god knows what kind of uber head ache.

I am relieved that you responded. And very prompt too!

@ woodmaster: 

Hi there,

I am tempted to give your solution a try. However, things are working and I dare not poke the sleeping beast.. :D
Thanks for sharing your solution. If the problem should repeat I'll give it a shot. I'm hoping for the best that it doesn't though.

I am so used to Windows (cause I've been a windows user almost all my life). Ubuntu is awesome, there is an element 'X' that satisfies me. I'm loving it (...that's Coca Cola, right?)

Cheers!

---

### Post by Iamwithin on 2011-06-08
Thank you sooo much!
This is why I love Ubuntu and Linux in general.
Your solution at the command line worked perfectly. :D

Bill

---

### Post by fixitdude on 2011-06-08
Don't you think the upgrading program should take care of all this?

Shouldn't it detect if the guy isn't updated and all that?

Please comment in this thread, this really has to stop.

"Why are Ubuntu upgrades still so much trouble?"
[http://ubuntuforums.org/showthread.php?t=1777864](http://ubuntuforums.org/showthread.php?t=1777864)

It only takes a little time to clean this upgrade process up, just a little extra thinking and a little extra care before releasing a upgrade program.

Not "it's done, it worked once, ship it !"

---

### Post by Old_Grey_Wolf on 2011-06-09
> **fixitdude said:**
> Don't you think the upgrading program should take care of all this?

Shouldn't it detect if the guy isn't updated and all that?

[COLOR="Red"]**Please comment in this thread, this really has to stop.**[/COLOR]

"Why are Ubuntu upgrades still so much trouble?"
[http://ubuntuforums.org/showthread.php?t=1777864](http://ubuntuforums.org/showthread.php?t=1777864)

It only takes a little time to clean this upgrade process up, just a little extra thinking and a little extra care before releasing a upgrade program.

Not "it's done, it worked once, ship it !"

I will comment on this thread. I am the person that offered the solution quoted in previous posts.

You are confusing updates and upgrades! This thread was about updates. Some of what I describe bellow applies to upgrades as well. 

The update program can not be fool-proof. Sometimes a network outage interrupts an update, or a power outage interrupts and update, or someone has manually changed the sources.list file, or adds a repository that is not a standard Ubuntu supported repository, and so on.

There is not an operating system I have ever used that can deal with everything that my happen by accident or user intervention. Try powering off a computer that is installing (they all recover well if just the download is interrupted) Microsoft Windows updates, OS X updates, Solaris updates, BSD updates; then, see what happens. There are also some things that can occur when the update program isn't running; therefore, it can not deal with them. 

I offered a solution that works in many cases. It justs cleans up the mess that result from many of those accidents; unfortunately, not all of them.

When you use a computer you take some responsibility for your own actions, the performance of the ISP you choose to use, and the reliability of the utility company you choose to use. No operating system can be held accountable for your choices beyond its control. One of the things that people like about Linux is that you have more control (freedom!) over what you are allowed to do with your computer.

---


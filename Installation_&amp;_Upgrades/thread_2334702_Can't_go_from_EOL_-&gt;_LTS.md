---
title: "Can't go from EOL -&gt; LTS"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by uh-huh on 2016-08-21
Hi Forum:
I tried to upgrade from 15.10 to 16.04 using ```
$sudo do-release-upgrade
``` but got "No new release found". So I went on-line and found there were a few more hoops to go through. There was use -c and -d switches, there was ```
$sudo apt-get upgrade
``` and ```
$sudo apt-get dist-upgrade
```. Another page had about five of these ```
$deb http://old-releases.ubuntu.com/ubuntu/ xenial-xerus main restricted universe multiverse
```. deb? Not a command according to bash.

So, none of these work. I keep getting "No new release found" Don't tell me I have to back up everything and install from a boot-stick!

---

### Post by kansasnoob on 2016-08-21
About this:

```
deb http://old-releases.ubuntu.com/ubuntu/ xenial-xerus main restricted universe multiverse
```

You may (or may not) have to change the software sources to look in "old-releases" if the 15.10 repos have been closed. But, **and this is a big but**, you don't want it to say "xenial-xerus" because 16.04 = Xenial and it's repos are definitely still open until at least April 2019.

But first things first. Open the Software & Updates UI and under the Updates tab look at the bottom where it says Notify me of a new Ubuntu version. Make sure that is set to say long-term support versions only.

Next post the full output of these two commands here so we can see what's actually going on:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

We should be able to tell from that if the 15.10 repos are closed or not, or if you have some other problem.

---

### Post by uh-huh on 2016-08-21
huge file - couldn't post it - error was 'security token missing'

trying this [http://paste.ubuntu.com/23077229/](http://paste.ubuntu.com/23077229/)

---

### Post by deadflowr on 2016-08-21
You need to disable the mc3man mpv-test ppa.
Then run the apt-get update command again.
And then the apt-get dist-upgrade command.

> error was 'security token missing'
forum error? or apt error?
(I did not understand whether that was related to the file or to the forums unable to load the file)

---

### Post by uh-huh on 2016-08-22
Forum error. When I tried to post the output of commands suggested by kansasnoob nothing happened but that error 'security token missing'. So I uploaded it using pastebinit.

How do I "disable" mc3man mpv-test ppa?

---

### Post by grahammechanical on 2016-08-22
You could have posted the output from each command separately and enclosed the text in quote tags and the text would become scrollable.

You should disable all PPAs before upgrading to a newer version and also switch to an open source video driver. System Settings>Software & Updates>Other software tab to disable PPAs and Additional Drivers tab to change to the open source video driver.

Regards

P.S. Do not use the -d switch with do-release-upgrade. That will upgrade to the unfinished development version (yakkety yak). It will only have 9 months support when it is released in October.

---

### Post by uh-huh on 2016-08-22
> **grahammechanical said:**
> You could have posted the output from each command separately and enclosed the text in quote tags and the text would become scrollable.

I tried that originally, thus the error. Went to plan B. The paste is scrollable, Ctl-F [/CODE] and Ctl-F [CODE]works. An 'addict' would know that.

Thanks for the info, been awhile since I had to edit the repo.

But, why do I have to give PW every time I click the stupid box? Least sudo sticks around for a bit.

---

### Post by uh-huh on 2016-08-22
OK, I changed the repo settings and rebooted. Now, before I lay this to rest, what do I do?```
 $sudo do-release-upgrade
``` or ```
$sudo apt-get dist-upgrade
``` 

What is the difference?

One more thing: if this works, and I come back on 16.04, how do I do the [solved] thing?

---

### Post by deadflowr on 2016-08-22
```
sudo apt-get dist-upgrade
```
updates all packages within the current version of Ubuntu.

It does differ from the safer updating command:
```
sudo apt-get upgrade
```
in that the upgrade command only updates already install packages. It won't install any new packages.
The dist-upgrade command will also install new packages.
(Important to note that dist-upgrade may also remove packages if it's needed to satisfy the needs of a new package)

```
do-release-upgrade
```
will update Ubuntu's release version.

It's important to know that you more likely than not will need to run the dist-upgrade command first, in order to get the updated packages that will allow for the do-release-upgrade command to work.

So basically, best way to go about it is
```
sudo apt-get update
sudo apt-get dist-upgrade
do-release-upgrade
```

---

### Post by deadflowr on 2016-08-22
```
sudo apt-get dist-upgrade
```
updates all packages within the current version of Ubuntu.

It does differ from the safer updating command:
```
sudo apt-get upgrade
```
in that the upgrade command only updates already install packages. It won't install any new packages.
The dist-upgrade command will also install new packages.
(Important to note that dist-upgrade may also remove packages if it's needed to satisfy the needs of a new package)

```
do-release-upgrade
```
will update Ubuntu's release version.

It's important to know that you more likely than not will need to run the dist-upgrade command first, in order to get the updated packages that will allow for the do-release-upgrade command to work.

So basically, best way to go about it is
```
sudo apt-get update
sudo apt-get dist-upgrade
do-release-upgrade
```

---

### Post by uh-huh on 2016-08-22
I asked on irc #ubuntu and the consensus seemed to be to use do-release-upgrade only. So I did and it worked apparently. I'm now rockin 16.04. Thanks for all the help guys! Now how do I mark this solved?

---

### Post by deadflowr on 2016-08-23
>  Now how do I mark this solved?

My lazy answer:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by uh-huh on 2016-08-23
sorry for this - please disregard

---


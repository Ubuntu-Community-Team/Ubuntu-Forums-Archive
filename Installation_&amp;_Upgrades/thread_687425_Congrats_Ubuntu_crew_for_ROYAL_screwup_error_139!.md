---
title: "Congrats Ubuntu crew for ROYAL screwup: error 139!"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Odrodzona-Sarmacja on 2008-02-04
Congrats Ubuntu crew for ROYAL screwup: error 139! Microsoft couldn't do a better sabotage.

Now, how I suppose to use my xubuntu 7.10? Is there any way to install and remove programs without using apt-get now?

---

### Post by Carl H on 2008-02-04
Error 139 can be caused by a corrupted, buggy, or old version of GCC - unlikely in your case. Or possibly you have some problems with your hardware. 

Perhaps if you explained what you were doing when you got this error, you might get some proper advice.

---

### Post by hyperair on 2008-02-04
I agree with Carl H. If you could give proper information about your condition someone could help you fix it. But what you've done is just throw a tantrum in a forum and not given any relevant information aside from a cryptic error code.

---

### Post by manimal347 on 2008-02-04
Perhaps Odrodzona was just expecting a "free Windows." Sorry, but you're now using a *nix operating system, complete with most of the freedoms and hassles that characterize them. Under that pretty surface, you have to realize that many components of it are built on the hobbyist level, and that bugs are expected. Indeed, historically, we've been expected to help fix them ourselves.


As for your question, Debian/Ubuntu have three main packaging frontends: Apt-get/apt-cache, Aptitude, and Synaptic. People keep talking about how Aptitude behaves differently then Apt-get, so why not give it a try.

---

### Post by Odrodzona-Sarmacja on 2008-02-04
First I upgraded my xubuntu from ff to gg and everything worked perfect with exception of network manager error messages during start up, but networking was working... even when after a time it went crazy and I had to use *sudo ifup eth0* to get internet connection after a reboot. Then one january day after an update something went wrong with synaptic... I got lots of error 139 messages and i could not install or remove anything on my computer... Eh...

So after couple of weeks of this irritation, I finally installed clean xubuntu 7.10 from livecd and everything was okay at first. Then I updated it. Still everything was okay. Then I tried to install some programs I use to my fresh and clean xubuntu 7.10 install and i got hit by the error 139 bug again and nothing worked with synaptic again. No install and no removal. From what I noticed sunaptic failed in essense with configuration of already downloaded and installed into directories files.

So I read for hours on the topic. Nothing too wise... Lot's of confusion. Someone did trace bug to some problem synaptic/aptitude/apt-get had with some kind crazy-glue database... So I went about reinstalling xubuntu 7.10 afresh from livecd. Everything worked. So I went about updating it with updates, but with one exception. I did not updated:

*
libdb4.4 Berkeley v4.4 Database Libraries [runtime] from version 4.4.20-8.1ubuntu3 to version 4.4.20-8.1ubuntu3.1
*
*
maintainer: <b>UBUNTU CORE DEVELOPER</b> <ubuntu-devel-discuss@lists.ubuntu.com>
*

Then I went to install programs without any further problem. No problems so far with 139 error.

I also read some people traced the error 139 bug to some segmentation problems... So I am not much wiser on this 139 error right now, but i am happy to get rid off it for now anyway.

---

### Post by Odrodzona-Sarmacja on 2008-02-05
Okay I got this bug again. It is not error 139 any more. I read that some new line is missing at the end of "xlsatoms" file list.

This again disables my synaptic from removing any old or installing any new software.

I guess berkeley database update thingy ain't the perpetrator, but surely one of the other of the Ubuntu's screwie january upates IS.

I need just to know, which january update to **** list, so it won't screw with my synaptic manager. I don´t mind reinstalling ubuntu every 3 days, but disabling synaptic with a security update in it IS THE STUPIDIEST THING THE LOOSERS AT UBUNTU SECURITY UPDATES DID EVER.

So, which update I must avoid next time I install my Xubuntu 7.10? It is about 100 of these ghostly security updates when I install Xubuntu 7.10 from livecd. Surely it will be possible for me to run Xubuntu 7.10 without any updates until 8.04 if this question will stay unanswered.

WHICH ONE JANUARY SECURITY UPDATE SCREWS SYNAPTIC?

---

### Post by hyperair on 2008-02-05
No idea, but try a mixture of these commands:
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by Odrodzona-Sarmacja on 2008-02-05
These commands gave no results. Then I did "sudo aptitude -f install openarena"and the error message I get is:

"files list file for package `xlsatoms' is missing final newline" in

> (Reading database ... dpkg: error processing /var/cache/apt/archives/libopenal0a_1%3a0.0.8-4ubuntu2_i386.deb (--unpack):
 files list file for package `xlsatoms' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libopenal0a_1%3a0.0.8-4ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


This error is kind of new. It's code 1. Before code of error was 139. However the synaptic doesn't allow any removals or additions of software after this happens. Some folks say it is something database related. Some other say it is related with segmentation. I just need to know, which january security update DID IT, so I can avoid it in future and have synaptic working, when I reinstall now my Xubuntu 7.10... again.

---

### Post by Cannaregio on 2008-02-05
> **Odrodzona-Sarmacja said:**
> I don´t mind reinstalling ubuntu every 3 days

well, I surely would. 
A small rant about updatemaniacs.

One of the joys in GNU/Linux is that you almost NEVER have to reinstall. Server or box can run for ages without touching.

I begin to believe that the unmoderated updatemania is the main culprit of most of the problems we can read about on these forums.
Why do you actually have such an itch to update?
If your system is working well (and it should, once you have finetuned it) DO NOT TOUCH IT. Update ONLY stuff that you know about and really badly need (in my case, for instance, wine). And even in this case, read the specs, find out BEFORE updating if it is worth it.
And what about the nonsensical upversioning every six months?
If you want to play that game, go over to debian's sid.
Have onto your work/game box just Ubuntu LTS versions, change, if ever, every three years or so.
Keep the last gutsy frill-oriented compiz stuff for your experimental box. DO NOT PUT IT WHERE YOU REALLY WORK & PLAY. 
And then,also, do not complain when your experimental box will be screwed.

---

### Post by Odrodzona-Sarmacja on 2008-02-05
There is a reason why updates are commings from ubuntu security server. They are _recommended_ by Ubuntu as neccessary security updates. It's like that hole interent explorer, just you got it in mozzila firefox. Just you don't get update from mozzila, you download it from security server of Ubuntu to patch it up.

Plus Ubuntu crew patched Ubuntu 7.10 with this stupid autoupdater, which when even disabled still shows up on your destop in form of "update notifier". So it is the stupidiest addition imho the Ubuntu crew could ever invent to their instable Ubuntu. They went mad there or went on some heavy drugs with their entire team, when they came with that *notifier* thingy for updates.

Usually, when the updates gather about 100-200 you make update like a system upgrade. Some are also neccessary to get rid of some Ubuntu's bugs, which can be annoying if they cause some problems with your applications. That Ubuntu ain't specially stable is not a secret.

Plus the last, but not at least. Ubuntu 7.10 installer will force an update down your throat, when you install Ubuntu 7.10 and forget in the same time to disconnect it from internet and because sometimes connections with the ubuntu's busy servers die, then you can spend like 6 hours (specially if it is over 100-200 updates at once) wondering if install froze to death, or is it still progressing.

And on top of it I use Xubuntu, so Debian is like next natural step, right? :D

---

### Post by forestpixie on 2008-02-05
this appears to be the same method as all the other similar 'is missing final newline' errors I found maybe it'll help

[http://ubuntuforums.org/showpost.php?p=4139181&postcount=2](http://ubuntuforums.org/showpost.php?p=4139181&postcount=2)

---

### Post by Odrodzona-Sarmacja on 2008-02-05
I don't know the first part with rar but...

1. sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_old
2. sudo mkdir /var/lib/dpkg/info
3. sudo apt-get update
4. sudo apt-get -f install

did the trick. It moved the lame synaptic to install new stuff :D :D :D, which makes me so happy...

The only minor nuisanse I got was about 1000 lines with serious warning messages from dpkg with following message:

> dpkg:serious warning:files list file for package '<insert one of the installed packages name here>' missing, assuming package has no files currently installed

plus minor problem it is reinstalling every god damn thing it needs again, even if I have it already isntalled, but I guess it is the nature of this solution :D :D :D Most important is IT WORKS!

Thanks forestpixie! You're great!

BTW. Why Ubuntu Crew can not make removing that directory, as automatic part of Ubuntu 7.10 :P, specially as it is so neccessary for using it ? :D

---

### Post by forestpixie on 2008-02-05
bit happier now then :) 

when I was at the really pulling my hair out stage lasty year I found that searching for what appeared to be the 'standard' part of an error rather than making it 'package' specific worked wonders

also now I use the uboontu search engine a lot which seems to help somewhat, I know it's straight from google and it doesn't catch recent stuff but there yougo

---

### Post by forestpixie on 2008-02-05
please do not involve me in arguments - all I did was use a search engine to search for the error, which you obviously didn't do yesterday when you started your rant

Do not shout in these forums - if you don't like something ignore it

Everyone here helping is doing so out of the kindness of their heart - and all that sort of post will achieve will be a 'oh yea I remember that name' :(

---

### Post by ugm6hr on 2008-02-05
I have removed 2 posts which were unnecessarily inflammatory.

Given that it appears that the problem is now solved, I have closed the thread.

If there are outstanding issues, please start a new thread with relevant details.

---


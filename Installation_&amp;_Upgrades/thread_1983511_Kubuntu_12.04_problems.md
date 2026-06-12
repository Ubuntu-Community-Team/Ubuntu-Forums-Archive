---
title: "Kubuntu 12.04 problems"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2012-05-20
Just installed Kununtu 12.04 (alternate CD version, fully encrypted ).  Problem 1: There is a CD reading noise for no reason (nothing running and there is no CD). So the computer is never completely quiet.   Problem 2: Muon doesn't work. Nothing can be installed from command line or Muon. Muon doesn't show what Adept shows in K 8.04. 8.04 was extremely good. 12.04 is extremely bad. Although it is supposed to be secure, nothing works. Nothing can be done. Can't install firefox, adept, synaptic or anything else. Should I uninstall some programs like Muon first to make sure things (like command line installations) work?   If 8.04 was encrypted I would never ever try to upgrade to any other version.  (Also want to understand what is the motivation behind making things not work by default.)  Thanks in advance.

---

### Post by darkod on 2012-05-20
Are you sure you have internet working correctly?

Note that some programs might not be available, so just because a program can't be found it doesn't mean there is a problem. Maybe it's not included in K12.04 any more.

Firefox should be there, but for example if Adept was replaced by Muon then Adept might not be available for installing any more, etc.

---

### Post by darkod on 2012-05-20
I just installed kubuntu 12.04 in virtual box to test, and installing from the terminal seems to be working just fine.

Inside Muon there seems it might have some issues when searching for a phrase/program, but the terminal is fine. I was able to install firefox and adept without any issues with:
sudo apt-get install firefox
sudo apt-get install adept

---

### Post by bjngchn on 2012-05-21
There is internet connection............Can use Rekonq browser........ Tried 3 different things for downloading firefox.........Muon: Doesn't work. It doesn't even see anything. When I search for firefox I only see firefox installer, which was already installed (part of 12.04). But it doesn't do anything. Click click click it says done, but nothing is done................................................................... Command line (terminal): doesn't work...............................................................................Downloading firefox for linux via Rekonq at mozilla web site, and unzipping (using Ark). Files named firefox don't work. Nothing happens when clicked................................................................. In short nothing works. Things should just work, but they just don't work. The best thing I get is  an error. Second best: things don't work, nothing happens, total silence. Worst thing: it is said things work when nothing happens. I spent one week still nothing happening.    ...............Also complained/and asked for help here:  ...............[http://ubuntuforums.org/showthread.php?t=1980678&page=2](http://ubuntuforums.org/showthread.php?t=1980678&page=2)

---

### Post by darkod on 2012-05-21
OK, lets focus on the terminal. What exactly doesn't work when you try it in terminal?

Do you have a server for the updates selected correctly, maybe the one selected is not working?

As I said, it installed without problems in terminal, both firefox and adept.

Yes, in Muon it seems when you want to search there are some issues, but installing in terminal worked straight away.

Don't forget it's not only internet access, you need a correct updates server set up so it can find them. Try with another server. Maybe that one doesn't work.

---

### Post by oldos2er on 2012-05-21
Can you post all the terminal output from ```
sudo apt-get update
``` ?

---

### Post by bjngchn on 2012-05-21
Yes, "update" from terminal was all that was needed. Thanks to all for help............... Still looking for "add-remove programs" tool (to remove Muon, which is not useful for me). Is a package manager needed to install or uninstlall from terminal? Can different managers (Muon, Adept, Synaptic,..) block eachother's actions? ......... (Main problems solved, but still appreciate more info, if any.)

---

### Post by oldos2er on 2012-05-21
You can only run one package manager at a time.

To remove muon, run ```
sudo apt-get remove muon
``` in a terminal.

---


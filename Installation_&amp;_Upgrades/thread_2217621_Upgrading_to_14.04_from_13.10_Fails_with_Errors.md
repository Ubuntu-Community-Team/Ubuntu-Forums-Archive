---
title: "Upgrading to 14.04 from 13.10 Fails with Errors"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by actionmystique on 2014-04-18
Hello,

I've had 2 errors during upgrading:
- non blocking man-db error:
[ATTACH=CONFIG]252160[/ATTACH]
- blocking python2.7 error:
[ATTACH=CONFIG]252161[/ATTACH]

Any suggestion before rebooting, which could probably not work well?

---

### Post by Dreamer Fithp Apprentice on 2014-04-18
Yeah. Burn some potentially useful cds for recovery before you reboot. A 14.04 live/install cd and Rescatux.  There are others rescue/utility/repair live disks iso around if you want to look a bit.

[URL="http://www.supergrubdisk.org/rescatux/"]http://www.supergrubdisk.org/rescatux/

Good luck.

Not sure why everything after the link looks like links. 
[/URL]

---

### Post by actionmystique on 2014-04-18
The problem now is...the usb stick is not automatically mounted after insertion.

---

### Post by Dreamer Fithp Apprentice on 2014-04-18
That means no cd burner?  Then I think I'd use startpage.com ('cause google is evil) and search for how to force a usb device to mount. I'm not real hopeful on that.  Dunno. I've never had a problem with sticks but I don't use then often. I think if it were me I wouldn't reboot until I had some kind of live disk or stick, preferably one of each. Maybe burn them at a library or a friend's place. At least for now you can use your computer.

Next time round, if you have hard drive space to spare, think about installing twice to 2 different partitons. If one goes bad, you can fix it from the other, at least if grub is still good.

---

### Post by actionmystique on 2014-04-18
I created a bootable DVD and rebooted: it went OK, at least so far.

I'm still trying to create that bootable USB stick (better than a DVD) with USB Creator and it does not work: it says there is not enough space, whereas the stick is empty:
[ATTACH=CONFIG]252170[/ATTACH] [ATTACH=CONFIG]252169[/ATTACH]

---

### Post by Dreamer Fithp Apprentice on 2014-04-23
That's odd. But I've only used thumb drives a few times, so what do I know? I suggest you mark this thread solved and start a new one with a title along the lines of:
"trying to make bootabe thumb, empty stick is reported as not having enough space."

---

### Post by actionmystique on 2014-04-24
I wouldn't call this thread "solved": the upgrading errors are still there and their effect on my system has not been determined.
[B][COLOR=#C61919][B]
sudodus[/B][/COLOR][/B]  	 has found a workaround for the making of a bootable USB stick issue: [http://ubuntuforums.org/showthread.php?t=2219251](http://ubuntuforums.org/showthread.php?t=2219251)

Thanks for trying to help.

---

### Post by Dreamer Fithp Apprentice on 2014-04-24
Yes, I re-read and I see what you mean. I was focused on the worry it wouldn't boot, but having gotten past that, you still haven't upgraded. Have you tried reinstalling the package the first error message complained about? Like:```
sudo apt-get install --reinstall man-db
```If that works ok, I'd try upgrading again. If it doesn't you might try```
sudo apt-get install -f
```and try again. I suggest keeping track of any error messages, and it if nothing works, post them.

---

### Post by actionmystique on 2014-04-25
I have upgraded already. The process did not complete though: it stopped at the second error.

---

### Post by actionmystique on 2014-04-25
Reinstalling man-db worked; trying to reinstall python failed.
The rest of the upgrading process has not been achieved.

---

### Post by actionmystique on 2014-04-25
Is there a way to test what's missing from the upgrading process, like a 14.04 system check?

---

### Post by Dreamer Fithp Apprentice on 2014-04-27
First of all, understand I'm out of my depth here. There are some real whiz-kids (or venerable geniuses as the case may be) around here, like Oldfred and Cariboo that might know what the stuff in your terminal about python really means, but not me. FWIW though I'd try aiming a search engine at assorted strings in that output you posted a picture of, the second picture. You could start with quoting the whole thing (surrounding it with "-marks to search the exact string supposedly, but it doesn't always work that way because a lot of non-alphanumeric characters choke the exact-string functions of every general web search engine I know of). My bet would be you'll just find this thread, but you might get lucky. I'd have done it myself but I can't copy text from a picture easily. The next step would be to search various substrings from that output. The last line about "SystemError: E . . ." sounds kind of promising.

I wonder just how much of the upgrade suceeded.  Do you get a 14.04 splash screen? ```
uname -a
``` will tell you your kernel. On a 32 bit version of 14.04 mine is 3.13.0-24-generic.

Since your error messages clearly had to do with python it couldn't hurt and might help to```
sudo apt-get install -f
sudo apt-get install python
```and if it replies something like "python is already the newest version"```
sudo apt-get install --reinstall python
```"python" is a metapackage or to quote synaptic "a dependency package, which depends on Debian's default Python version (currently v2.7)." I'd be curious to know the result.

If everything seems to be working you might check some version numbers to see if anything is older than you'd expect on 14.04. For instance ```
bash --version
```in a terminal gets me the response "GNU bash, version 4.3.11(1)-release (i686-pc-linux-gnu)". I'm not sure if you use any of these, but the same syntax works for firefox ( mine's 28.0 ), thunar (1.6.3 here), openbox (mine's 3.5.2), and conky (mine's 1.9.0). Wow, that must be nearly universal. It worked for everything I tried. Anyway you might want to check that for all the major programs you use, including window manager, file browser, etc. If luck is with you and python installs ok, everything you check seems to be the version it should be, and nothing you've tried seems broken, you might just bookmark this thread and keep any notes you made for future reference in case of some future problem you suspect might have originated in the upgrading, but otherwise assume you're good to go. If not, well, one bridge at a time.
====================
Added by edit a minute later:
I didn't notice there was a second page before replying and didn't see your "system check" idea. A good idea, I think. Not anything made for the purpose as far as I know. But it is possible with bash commands (that I'll have to look up) to make a list of installed packages. I don't know but it wouldn't surprise me if there was a way to get it to add version numbers to the list. You'd really want to get the reference list from somebody who had as similar a system as possible. Meaning 32 or 64 bit, vanilla Ubuntu w. Unity, etc  or some other flavor like Lubuntu, and so on for as many details as you can match. I can list my packages if you want but I'm afraid it would probably be more misleading than helpful as my system it pretty non-standard. I installed the mini.iso that gives you little more than bash, apt, basic drivers, and whatever you need to get to the internet with command line in a non-windowed tty and built it up from there. I use plain openbox (only openbox, not Lubuntu), xorg, lxterminal, and thunar but no "desktop". In other words, I ordered a la carte.

---

### Post by actionmystique on 2014-04-27
Regarding the kernel and bash versions, I have the same as yours.
Thanks to your help, I was able to successfully reinstall python to 2.7.5-5ubuntu3.

---

### Post by Dreamer Fithp Apprentice on 2014-04-27
Sounds like you probably have it licked. If a ```
sudo apt-get update
sudo apt-get dist-upgrade
```runs with no error messages, personally, I'd assume you were good to go. But if you want to investigate more thoroughly, I did do a little research, so here are the results:

The way to get a list of installed packages with version numbers is:```
dpkg -l
```To echo it directly to a text file:```
dpkg -l > /path/to/somefilename.txt
```To append output from another command (for instance, the same command done in a different partition) to the same file use ">>" instead of ">". So that part is easy. If you want to play around with bash a bit, you can probably come up with a command, or at least a set of commands, to run the outputs of dpkg -l done on different systems together and format them something like:

some-package-name
  13.10 version: 1234
  14.04 version: 5678

another-package
  13.10 version: 1.4.2
  14.04 version: 3.1.4.1.5.9.2.6.5

If you want to try to write a script to do that, if you aren't already familiar with them I'd look at the mans for commands like grep, sed, and cut. With those you can probably come up with some way to create a file with a format like that. If you think that is worth the effort and you succeed, post the script.

Attached are 2 archives (both with the same content, I just made 2 in case you have problems with either format you can use whichever is more convenient) with 2 text files, one with the installed package list with version numbers for a 13.10 updated today and another with the same for a 14.04 updated today. Caveat: Neither system is anywhere near being a standard installation, and furthermore they are tweaked very differently so they won't have the same list of packages, but whatever you find in there that is on both lists, but with different version numbers, it is highly likely the version numbers are the correct current ones for those Ubuntu versions, at least for the 32 bit varieties. So there's proof of concept at the very least. You can be even more thorough if you get someone with a 14.04 system very similar to your own to make the same list for you.

---

### Post by actionmystique on 2014-04-28
Thanks for your work!
Updating my system with Synaptic leads to no error, no broken packages.
I have made a list of all my packages with their version number; however, it is not possible to compare them with yours, since my system is 64 bits. On top of that, that would be too much work.

There must be another way: since the upgrading process stopped at the "python" package, I wondered whether this process was trying to update all packages in an alphabetical order; in which case, it might be possible to try to reinstall all my installed packages listed "below" python with a simple script. Would this make sense and be necessary since the update with Synaptic passes?

---

### Post by oldfred on 2014-04-28
It used to be that if you uninstalled python, that you might as well just totally reinstall. Just about everything was dependant on python. 
Now some have been able to recover from that, but I am not sure of details.
As noted below they are trying to convert everything from python2 to python3 where each is most current version.

If you want a list of default installed packages see the manifest list for your version.
[http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

Info on changes:
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Updated_Packages](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Updated_Packages)

---

### Post by actionmystique on 2014-04-28
If I understand correctly the transition to Python 3, I should have this release on my system with all dependant packages recompiled with this new version.

I have Python 3.4.0. I've checked all the versions of the packages listed [here]("http://people.canonical.com/~ubuntu-archive/transitions/onlypy3oncd.html") with the ones on my system. They all match except the following which are not present:
- landscape-client and landscape-client-ui: I have only landscape-client-ui-install
- python-libvirt
- python-[paramiko]("https://launchpad.net/ubuntu/+source/paramiko")
- [python-boto]("https://launchpad.net/ubuntu/+source/python-boto")
- [python-cloudfiles]("https://launchpad.net/ubuntu/+source/python-cloudfiles")
- [quickly]("https://launchpad.net/ubuntu/+source/quickly")
[- rastertosag-gdi]("https://launchpad.net/ubuntu/+source/rastertosag-gdi")
- [ndisgtk]("https://launchpad.net/ubuntu/+source/ndisgtk")
- [pidgin]("https://launchpad.net/ubuntu/+source/pidgin")

Do I need to install all these packages or is there some recompilation involved somehow?

[I]_**P.S**_: Regarding **LibreOffice**, I don't think it's a good idea to distribute an unstable RC by default.
[/I]

---

### Post by Dreamer Fithp Apprentice on 2014-04-28
You might look up all but the lib (python-libvirt) and see what they are. I don't think you need to worry about libraries (normally named lib-something) unless you have something broken that depends on them or you get some error message complaining of their absence. If something you are using needs them apt should take care of that. If they are applications with clear information as to what they are for I wouldn't bother unless they are something you want to use.  You can always install them later if you develop a use for them. If if looks like it might be something the system uses behind the scene, you might want to try to install it. If Oldfred drops back by, he might be more explicit. If it looks like something that is only on the list because something else depends on it, I wouldn't bother unless and until you get some sort of error message calling for it. There is a line at the bottom of synaptic that will tell you how many broken packages there are. If it isn't 0 you might want to click "custom filters" on the left and then "broken" to see what they are.

---


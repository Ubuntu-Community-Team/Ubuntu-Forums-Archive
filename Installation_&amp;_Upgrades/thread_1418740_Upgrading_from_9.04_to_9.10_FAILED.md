---
title: "Upgrading from 9.04 to 9.10 FAILED"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by paopao on 2010-02-28
Just to note, I'm rather a novice and only have been using Ubuntu for a short time.  Previously when I upgraded from 8.10 to 9.04 I had massive errors, so I just did a clean install (I had data backed up).

I do have all the data backed up (although installing all the programs and re-doing the various settings will take some time and be annoying); so if I need to do a clean install, then it's OK.  However, since this is the second time this happened, I should learn how to do it correctly; especially since my server (another computer running 9.10 server edition) will have issues in April 2011 and I might not have large enough hard drives to backup the data.


My apologizes for the rather uninformative error messages, I didn't write them down.

So, I went to the update manager and selected to upgrade to 9.10.  It worked fine at first, telling me a list of programs were no longer supported and would be uninstalled (most of them libraries that I didn't know what they did).  Then it complained about the program "apt" that seemed rather serious, but I let it continue.  Eventually, it just decided to fail at the installation (it said it failed and would leave the computer in an unstable state and that I should submit a bug report with the contents of some file that I've forgotten what it was).  It then said that it would run the command "dpkg --configure -a" to try to recover the upgrade.  It ran that command, and then also failed.

So I restarted the computer.  It didn't load graphically, rather directly to the shell.  I could log in.  I ran the command "dpkh --configure -a" again and it showed a bunch of text and then stopped with the last line reading, "Processing was halted because there were too many errors."


It's kind of annoying because this was the second time that the upgrading failed and left my computer in an unstable state.  Which makes me wonder - did I upgrade wrong?  How could I, there's only one button to press.  Did I install too many programs from the default installation that caused the upgrading process to fail?  If so, what programs caused this?  Or is the upgrading program just that unstable - seems rather unlikely given the age of Ubuntu.  I'm certain that I did something to screw this up.

I made a list of programs that I installed so that I could install them after a complete OS reinstallation:
bomberclone bomberclone-data flashplugin-nonfree gparted ruby irb language-pack-gnome-zh language-pack-gnome-zh-base language-pack-zh language-pack-zh-base language-support-extra-zh language-support-fonts-zh language-support-input-zh language-support-translations-zh lbreakout2 lbreakout2-data mozplugger m4 okular ssh scim skype texlive-full vlc

lamp-server* nautilus-image-converter nautilus-open-terminal mediawiki

(although, it's quite possible that there are many more that I installed and neglected to make a note of installing them).



So.  I apologize for lack of information where information is needed and too much information for where information is not needed.  If anyone is willing to help me upgrade (without doing a clean reinstall), and also possibly tell me what I did to botch the upgrading process - that'd be great.  I'm certain that I'll have to provide more information, so I will, if asked.



Lastly, is there a possible way of doing a "test" upgrade, in which it goes through the process without really going through the process so that I could see if the program yields errors without leaving my system in an unstable state?

---


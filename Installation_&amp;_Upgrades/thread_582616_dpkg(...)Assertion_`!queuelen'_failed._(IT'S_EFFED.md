---
title: "dpkg:(...)Assertion `!queuelen' failed. (IT'S EFFED!)"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Hoppiesbox on 2007-10-20
I've searched these forums for hours now using a Live CD, and am sorry to say I haven't seen anyone with a similar problem yet (*,)

After the long overnight and half the next morning download, while the packages were being updated...I returned to the computer to find that the update had apparently finished. Hooray I thought! I noticed many programs had changed their icons, so clearly some things had changed...but the system never restarted, and I never saw the "cleaning up" part happen. Curious...

My wife was eager to get a blog written or some other such thing, and so despite my better judgement (I knew I shouldn't have tempted fate) I switched users...

After exiting my session, it just hung at a screen looking like the login window was going to appear at any moment...but alas, not. (the computer still gets to this point after booting, and I am able to ctrl-alt-F1 and work from there)

I could guess and guess at this point about the problem, I did take a look at the log files in var/log/dist-upgrade 

the end of term.log:
```
gconftool-2: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing libgnomekbd-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up bsdmainutils (6.1.6ubuntu1) ...
Setting up util-linux-locales (2.13-8ubuntu1) ...
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
Setting up discover1-data (2.2007.05.11ubuntu4) ...
Setting up dmz-cursor-theme (0.4.1) ...
Setting up libxfce4util4 (4.4.1-1ubuntu1) ...
Setting up screen (4.0.3-0.4ubuntu2) ...
Installing new version of config file /etc/init.d/screen ...
 Removing any system startup links for /etc/init.d/screen-cleanup ...
dpkg: dependency problems prevent configuration of libgdl-gnome-1-0:
 libgdl-gnome-1-0 depends on libgnomeui-0 (>= 2.17.1); however:
dpkg: error processing libgdl-gnome-1-0 (--configure):
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.
```

This seems like a biggie to my noobie eyes - I've tried 'sudo dpkg --configure -a' like every apt related command tells me to, but get the same output.

PLEASE let me know what other info might be helpful - I know there is a slew of tough questions on the boards right now.

THANKS for the help everyone, keep up the good work!

---

### Post by Hoppiesbox on 2007-10-20
*bump*
Before bed I burned (at the command line, how cool) the .iso I downloaded lastnight - the 'alternate cd' 
Today I plan on backing up my home folders and other things so I can try upgrading/fresh install via that cd. Does anyone have any advice about that procedure relating to keeping all my settings and what-not?

Can anyone provide a list of folders to backup to make sure that my new system is as close to my old setup as possible? I'm guessing that packages will have to be reinstalled, but will the programs have all the same plugins/saved settings as before?

If anyone can help me get my old setup back though, that'd be super. I'd rather not just give up :(

---

### Post by EnterDaMatrix on 2007-10-20
I believe that all (most) the settings are stored in the home folder. If you made a home partition at install you should be able to overwrite the other partitions and start fresh. I'm having the same problem and this is what I plan to do. It's pretty pathetic in my opinion, but right now its the best option because there is no solution.

---


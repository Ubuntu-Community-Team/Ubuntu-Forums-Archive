---
title: "Firefox 3 beta 4"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by white_eagle-mk on 2008-03-11
How can I replace the original Firefox 2.x with Firefox 3 Beta 4 which is currently out? 
And no, I don't want the firefox-3.0 package in the repos because that is FF 3 Beta 3 which is unstable for me, dunno why, and FF 3 beta 4 is very much stable.... 
So... help ;)

---

### Post by atoc on 2008-03-11
> **white_eagle-mk said:**
> How can I replace the original Firefox 2.x with Firefox 3 Beta 4 which is currently out? 
And no, I don't want the firefox-3.0 package in the repos because that is FF 3 Beta 3 which is unstable for me, dunno why, and FF 3 beta 4 is very much stable.... 
So... help ;)

Just download the tarball and run it from your home directory.

---

### Post by white_eagle-mk on 2008-03-12
NO, I have it that way, I want it to replace FF 2.0

---

### Post by jkrtest on 2008-03-12
OK, maybe this will work for you: 
Backup your profile
Before you run Firefox, you may want to backup your profile from Firefox 2. I haven&#8217;t had any problems sharing the profile so far, but don&#8217;t let Firefox 3 update update your extensions when it starts to avoid incompatibilities. This command will backup the Firefox profiles folder to firefox_profile_backup in your home folder:
cp -r ~/.mozilla/firefox/ ~/firefox_profile_backup

If you need to restore from the backup, do so by replacing the hidden .mozilla/firefox folder with your backup.

Install Firefox 3 Beta 4
Let&#8217;s install Firefox now. The command below does two things: it downloads Firefox to your home directory using wget, and extracts the Firefox folder there. Copy and paste the command (it&#8217;s one line) and run it in your terminal:
wget -P ~ [ftp://ftp.mozilla.org/pub/firefox/releases/3.0b4/linux-i686/en-US/firefox-3.0b4.tar.bz2](ftp://ftp.mozilla.org/pub/firefox/releases/3.0b4/linux-i686/en-US/firefox-3.0b4.tar.bz2) && tar xjf ~/firefox-3.0b4.tar.bz2 -C ~

Once that command has completed, you can delete the firefox-3.0b4.tar.bz2 file in your home directory.
rm ~/firefox-3.0b4.tar.bz2

Run Firefox 3 Beta 4
Before running Firefox 3, close Firefox 2. Double-click the firefox file inside the firefox folder in your home directory, or run this command:
~/firefox/firefox

You can add Firefox 3 to your GNOME Applications menu using the menu editor in System->Preferences->Main Menu.

NB: I copied this from a web site which I can't find anymore. Apologies to the original author.
I tries this and it worked like a charm.
Dunno if it "replaces" v2 files. I don't know where to look for them.

---


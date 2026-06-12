---
title: "After upgrade to 11.10 can not install Dropbox"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2011-11-01
I have used DB for a couple of years now and have  it installed on a number of machines and my mobile.  I have also got my  accountant to use it to share files, so I think I am quite aware of the  app - and a great one it is too.  However, I have just upgraded to  Ubuntu 11.10 from 11.04 on my main PC and it refuses to install.  It  shows up on the App store and when clicks it tries to install.  It  downloads, but it stops at 97% when installing.  Every time.  I have  tried un-installing and did find (though I can't find it again) a thread  on the Ubuntu Forum that discusses this.  I tried it and thought it had  worked until I restarted my PC and found it had reverted.
:(

 Can you please advise HOW I un-install completely and then reinstall the app?

---

### Post by magic8ball on 2011-11-04
Hi,

I recently did a fresh install of 11.10 and loaded DB without problems.

I don't know how to completely uninstall DB, sorry.

When I loaded DB, I used the appropriate installer from the DB website.  It was newer than the version in the Software Center.  I got it from:

[http://www.dropbox.com/downloading?os=lnx](http://www.dropbox.com/downloading?os=lnx)

Good luck.

---

### Post by raja.genupula on 2011-11-04
> **Jonners59 said:**
> I have used DB for a couple of years now and have  it installed on a number of machines and my mobile.  I have also got my  accountant to use it to share files, so I think I am quite aware of the  app - and a great one it is too.  However, I have just upgraded to  Ubuntu 11.10 from 11.04 on my main PC and it refuses to install.  It  shows up on the App store and when clicks it tries to install.  It  downloads, but it stops at 97% when installing.  Every time.  I have  tried un-installing and did find (though I can't find it again) a thread  on the Ubuntu Forum that discusses this.  I tried it and thought it had  worked until I restarted my PC and found it had reverted.
:(

 Can you please advise HOW I un-install completely and then reinstall the app?


actually to uninstall a app completely we can use this command

```
sudo apt-get remove --purge <app>
```

---

### Post by Jonners59 on 2011-11-04
Thanks guys
I managed to get a fix for this problem from Stefano at Dropbox.  Have just tested and it works.  Please find below the steps:

[HTML]$ wget http://dl-web.dropbox.com/u/17/dropbox-lnx.x86-1.2.48.tar.gz
$ dropbox stop[/HTML] Dropbox status # Should report "not running"

[HTML]$ mv ~/.dropbox ~/dropbox.old
$ tar xzf dropbox-lnx.x86-1.2.48.tar.gz
$ dropbox start -i[/HTML]Only issue was the following message after install during set up which relates to folder permissions.  Still figuring it out as after opening as Administrator (right click menu) and changing the perms I still get the files locked as root owned.

[HTML]** (nautilus:2915): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2915'[/HTML]This is a permissions problem.  There are plenty of threads on fixing, but here are Stefano's instructions:


1) Stop the Dropbox desktop application (if needed)

- Click on the Dropbox icon.
- Choose Quit/Stop/Exit

2) Open a Terminal 

3) Copy and paste the following lines into the Terminal, one at a time, and press RETURN after each one. PLEASE make sure you copy and paste these commands (don't type them by hand), as getting them wrong could cause some harm. You'll be prompted for your computer user's password (not your Dropbox password) after entering the first command.

```
sudo chown "$USER" "$HOME"
```
```
sudo chown -R "$USER" ~/Dropbox ~/.dropbox
```

```
sudo chmod -R u+rw ~/Dropbox ~/.dropbox
```

4) Restart Dropbox from Applications

ENJOY:)

---


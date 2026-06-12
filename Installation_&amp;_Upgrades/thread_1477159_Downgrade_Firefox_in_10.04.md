---
title: "Downgrade Firefox in 10.04?"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by d0rp on 2010-05-08
I just upgraded to 10.04, and am quite happy with it so far, but it installed Firefox 3.6, which is a problem for me because I need to be able to use the Jssh plugin, which isn't available for 3.6 yet.

All I need to do is downgrade Firefox to 3.5, but I seem to be having some issues, it seems that there is only the one version available to me in Synaptic. Is there another repository that I need to add to have access to an older version?

---

### Post by aysiu on 2010-05-08
You can download the the .tar.bz2 from the Mozilla website and use that until the Jssh plugin gets updated:
[http://www.mozilla.com/products/download.html?product=firefox-3.5.9&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-3.5.9&os=linux&lang=en-US)

Once you download them to, say, your Downloads folder, **paste** (do not retype) these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) (probably best to close Firefox before doing all this... you can paste these into a text file in the meantime): ```
cd ~/Downloads
cp -R ~/.mozilla ~/.mozillabackup
sudo tar -C /opt -jxvf firefox-3*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.old
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` In case you're curious, these are what the commands do:
Change focus to your Downloads directory (this is presumably where the .tar.bz2 you downloaded went).
Make a backup copy of your Firefox settings, history, and bookmarks.
Extract the downloaded .tar.bz2 compressed file to a directory.
Rename the empty plugins folder.
Link your Firefox plugins to the new Firefox.
Rename the old Firefox 3.6 launcher to the command *firefox.ubuntu*.
Link the new Firefox 3.5 to the command *firefox*.

So if you want to launch Firefox 3.5, you can do so by just clicking the Firefox icon.

If you want to launch Firefox 3.6 (say, when the plugin you want gets updated), you can launch it with the command *firefox.ubuntu*

---

### Post by nerdy_kid on 2010-05-08
you might be able to coerce the extension to work with 3.6.  If you download and extract it there is an xml file that limits the firefox versions that it can be installed on.

---

### Post by d0rp on 2010-05-08
Thanks! That worked. :)

---

### Post by daleslcap on 2010-05-26
I followed all these steps but I come up with the following error when trying to run the command firefox
/opt/firefox/run-mozilla.sh: 399: /opt/firefox/firefox-bin: not found
however the file does exist in the proper directory
Here is the output from locate
dale@dale-desktop:/opt/firefox$ locate firefox-bin
/opt/firefox/firefox-bin
/usr/lib/firefox-3.6.3/firefox-bin

I need to downgrade because the vmware console plugin won't work in Firefox 3.6.3

Any help would be appreciated

Thanks in advance

---

### Post by aysiu on 2010-05-26
> **daleslcap said:**
> I followed all these steps but I come up with the following error when trying to run the command firefox
/opt/firefox/run-mozilla.sh: 399: /opt/firefox/firefox-bin: not found
however the file does exist in the proper directory
Here is the output from locate
dale@dale-desktop:/opt/firefox$ locate firefox-bin
/opt/firefox/firefox-bin
/usr/lib/firefox-3.6.3/firefox-bin

I need to downgrade because the vmware console plugin won't work in Firefox 3.6.3

Any help would be appreciated

Thanks in advance
Any chance you're running 64-bit Ubuntu?

---

### Post by n1ght5t4lk3r on 2010-05-26
> **nerdy_kid said:**
> you might be able to coerce the extension to work with 3.6.  If you download and extract it there is an xml file that limits the firefox versions that it can be installed on.

the "mr.tech toolkit"  [https://addons.mozilla.org/en-US/firefox/addon/421](https://addons.mozilla.org/en-US/firefox/addon/421)  addon in firefox also overrides max version compatibility of addons (amongst hundreds of other functions), in the list of installed addons just right click on the desired addon and "make compatible" then restart firefox, saves extracting the mentioned file and changing stuff

---

### Post by daleslcap on 2010-05-26
> **aysiu said:**
> Any chance you're running 64-bit Ubuntu?

Yes 64 bit

---

### Post by daleslcap on 2010-05-26
> **n1ght5t4lk3r said:**
> the "mr.tech toolkit"  [https://addons.mozilla.org/en-US/firefox/addon/421](https://addons.mozilla.org/en-US/firefox/addon/421)  addon in firefox also overrides max version compatibility of addons (amongst hundreds of other functions), in the list of installed addons just right click on the desired addon and "make compatible" then restart firefox, saves extracting the mentioned file and changing stuff

Installed "mr.tech toolkit" 
uninstalled vmware plugin
reinstalled vmware plugin checked the compatibly box 
still can't get console to run

---

### Post by shawndearmond on 2010-05-26
I'm having exactly this problem as well.  I have 10.04 64bit running VMWare Server, and I need to get the Remote Console plugin working.  I followed the directions above, but am getting the same result as daleslcap.

---

### Post by n1ght5t4lk3r on 2010-05-26
yeah sorry to the OP, my reply wasn't really aimed at you and your issue and more just a suggestion to the guy I quoted, on an easier method of doing that which he mentioned

---

### Post by Vannak on 2010-05-26
> **aysiu said:**
> You can download the the .tar.bz2 from the Mozilla website and use that until the Jssh plugin gets updated:
[http://www.mozilla.com/products/download.html?product=firefox-3.5.9&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-3.5.9&os=linux&lang=en-US)

Once you download them to, say, your Downloads folder, **paste** (do not retype) these commands into [the terminal]("http://www.psychocats.net/ubuntu/terminal") (probably best to close Firefox before doing all this... you can paste these into a text file in the meantime): ```
cd ~/Downloads
cp -R ~/.mozilla ~/.mozillabackup
sudo tar -C /opt -jxvf firefox-3*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.old
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` In case you're curious, these are what the commands do:
Change focus to your Downloads directory (this is presumably where the .tar.bz2 you downloaded went).
Make a backup copy of your Firefox settings, history, and bookmarks.
Extract the downloaded .tar.bz2 compressed file to a directory.
Rename the empty plugins folder.
Link your Firefox plugins to the new Firefox.
Rename the old Firefox 3.6 launcher to the command *firefox.ubuntu*.
Link the new Firefox 3.5 to the command *firefox*.

So if you want to launch Firefox 3.5, you can do so by just clicking the Firefox icon.

If you want to launch Firefox 3.6 (say, when the plugin you want gets updated), you can launch it with the command *firefox.ubuntu*What's the syntax to change it back with ln, so that I can make "firefox" run 3.6 again?

---

### Post by aysiu on 2010-05-27
> **Vannak said:**
> What's the syntax to change it back with ln, so that I can make "firefox" run 3.6 again?
I believe the commands are ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

---

### Post by daleslcap on 2010-05-27
I got mine running outside firefox following instructions here

[http://www.geeklab.info/2010/02/running-vmware-remote-console-outside-the-browser/](http://www.geeklab.info/2010/02/running-vmware-remote-console-outside-the-browser/)

used the vmware-vmrc-linux-x64.xpi from my machine

maybe we need firefox 3.5 64 bit

---

### Post by samwisekoi on 2010-07-28
Did not work for me.  Firefox came up in 3.6.8 (clicked icon, selected from Applications, entered "firefox" at the CLI.)

Hmmm.  THIS computer is still on jaunty.  I'll keep trying.

 - Sam

p.s.  Trying (and failing) to get to the VMware console.

> **aysiu said:**
> You can download the the .tar.bz2 from the Mozilla website and use that until the Jssh plugin gets updated:
[http://www.mozilla.com/products/download.html?product=firefox-3.5.9&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-3.5.9&os=linux&lang=en-US)

Once you download them to, say, your Downloads folder, **paste** (do not retype) these commands into [the terminal]("http://www.psychocats.net/ubuntu/terminal") (probably best to close Firefox before doing all this... you can paste these into a text file in the meantime): ```
cd ~/Downloads
cp -R ~/.mozilla ~/.mozillabackup
sudo tar -C /opt -jxvf firefox-3*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.old
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` In case you're curious, these are what the commands do:
Change focus to your Downloads directory (this is presumably where the .tar.bz2 you downloaded went).
Make a backup copy of your Firefox settings, history, and bookmarks.
Extract the downloaded .tar.bz2 compressed file to a directory.
Rename the empty plugins folder.
Link your Firefox plugins to the new Firefox.
Rename the old Firefox 3.6 launcher to the command *firefox.ubuntu*.
Link the new Firefox 3.5 to the command *firefox*.

So if you want to launch Firefox 3.5, you can do so by just clicking the Firefox icon.

If you want to launch Firefox 3.6 (say, when the plugin you want gets updated), you can launch it with the command *firefox.ubuntu*

---

### Post by aysiu on 2010-07-28
> **samwisekoi said:**
> Did not work for me.  Firefox came up in 3.6.8 (clicked icon, selected from Applications, entered "firefox" at the CLI.)

Hmmm.  THIS computer is still on jaunty.  I'll keep trying.

 - Sam

p.s.  Trying (and failing) to get to the VMware console.
Is your Firefox 3.6.8 from the Ubuntu repositories or from the Mozilla website? Have you used UbuntuZilla before?

If you had previously "installed" 3.6.8 using UbuntuZilla or using a .tar.bz2 file from the Mozilla website, the instructions I gave will **not** work.

---

### Post by samwisekoi on 2010-07-28
UPDATE:

I found a solution path.  I can START VMware servers via FF 3.6.8, and then use Terminal Server to RDC to them.  (VMware is how I do things that require Windows.)

My FF upgrade came with the normal daily stream from Canonical for Jaunty.  I have not used UbuntuZilla or installed from a .tar file.

But since I can now SEE my XPVM, I will be moving to Virtualbox and removing the browser connection to my VMs.

 - Sam

> **aysiu said:**
> Is your Firefox 3.6.8 from the Ubuntu repositories or from the Mozilla website? Have you used UbuntuZilla before?

If you had previously "installed" 3.6.8 using UbuntuZilla or using a .tar.bz2 file from the Mozilla website, the instructions I gave will **not** work.

---

### Post by bethnesbitt on 2011-03-02
I just wanted to say thank you, this worked for me in Ubuntu 11.04 alpha.  I was having issues where my mic and my video card where not working properly in 10.04 so I decided to upgrade to 11.04, and now they work, but unfortunately, some addons are not compatible yet with firefox 4x beta.  Google video and chat for example is one plugin that is not yet compatible with firefox 4.  Once I downgraded back to firefox 3.6x, everything worked beautifully! :D

---

### Post by dinsdalepirhana on 2011-07-12
Thank you Asiyu, this worked great for me.  Needed this to get vmware server console working again.  instructions were perfect, you saved me lots of time!

---


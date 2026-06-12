---
title: "true type font install problems"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by dsimpson on 2006-12-07
I downloaded and installed msttcorefonts and it affects my ability to run realplayer10gold, gnucash although I think the problem isn't with the font download but with another file which is needed to complete my downloads and installs. I get the following message:

E:msttcorefonts: subprocess post-installation script returned error status 1

Has anyone else seen this problem or is there a remedy for it that I haven't found yet? I really need help with this, it seems to be affecting all my downloads. I think it is affecting my use of Automatix also, I get an error message that says a key is could not be downloaded.

---

### Post by linear on 2006-12-07
> **dsimpson said:**
> E:msttcorefonts: subprocess post-installation script returned error status 1

The msttcorefonts package provides scripts that automate the process of getting and installing the fonts. The error simply means that something went wrong during the running of the script; possibly it was unable to get one or more of the fonts.

Are you located behind a proxy server, by any chance? If so, you need to tell **wget** about the proxy server (edit **/etc/wgetrc**; if you need more instruction see [here]("http://ubuntuforums.org/showpost.php?p=541276&postcount=1006")).

If you're not behind a proxy, try installing the package from a terminal window (**sudo apt-get install msttcorefonts**) and look for error messages in the output.

---

### Post by boussetta on 2006-12-08
I am having the same problem and it seems that s due to the internet connection and as I am new to linux I cannot figure out any solution for the moment.
the error message is: 
"...... [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--16:58:56--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)"

---

### Post by dsimpson on 2006-12-08
Bousetta, I used the link after the comment about wget on the post prior to yours from linear, and changed the address to my local ip address and everything seemed to be working now. I hope this can help you also, it is kind of confusing for a newbie but after entering a couple of times I got it to work. Good luck

---


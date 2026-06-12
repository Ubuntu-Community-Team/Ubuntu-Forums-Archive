---
title: "Keeping Firefox up to date on Lucid after end of support"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by mikechant on 2013-06-28
10.4/Lucid Desktop version is now out of support. I know I should upgrade but I'm still weighing the options etc. and in the mean time I want to at least keep Firefox and Flash player up to date (would cover 95%+ of security issues).
Any suggestions as to the least painful method? Particularly any relevant ppas? I've searched generally and on this forum and not found anything useful yet.

---

### Post by snowpine on 2013-06-28
There is a magical website where you can always find the latest Firefox: [http://firefox.com](http://firefox.com)

---

### Post by mikechant on 2013-06-28
> here is a magical website where you can always find the latest Firefox:

I realize I can get a tarball to install manually. As I stated, I was particularly hoping for a ppa, which would then form part of the normal update process without me having to update manually every few weeks. Or possibly a deb package, so at least it would be tracked by the package manager.

---

### Post by Frogs Hair on 2013-06-28
Any PPA's will not likely be maintained unless provide by a user like yourself   . The main problem I foresee is dependencies for Firefox and Flash . While you can add the Ubuntu old release source list this will not include anything new . [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

AFAIK you will have to build or install new version from tar.gz files and there is information for Firefox on the web. Ubuntu post 11.04 is using Gnome 3, so libraries and other dependencies have and will change.

---

### Post by snowpine on 2013-06-28
> **mikechant said:**
> I realize I can get a tarball to install manually. As I stated, I was particularly hoping for a ppa, which would then form part of the normal update process without me having to update manually every few weeks. Or possibly a deb package, so at least it would be tracked by the package manager.

Who is going to waste their time making a PPA for an obsolete Ubuntu release? There is no "normal update process" for end-of-life releases because there are not and never will be any more updates!

Running the latest firefox from firefox.com is super-duper easy: Just double-click to extract the tarball, then double-click the Firefox executable. (Just like a .zip with a .exe inside for Windows.) If that's challenging for you then I don't think running an obsolete OS with no security/stability patches is a good idea for your skillset. ;)

---

### Post by mikechant on 2013-06-28
> Who is going to waste their time making a PPA for an obsolete Ubuntu release? 
10.4 is not just any old obsolete release. It's the last Gnome 2 LTS, and a lot of people would have stuck with it if possible (e.g. if it had 5 years support like the current LTS desktop versions). This is exactly the sort of thing I would have hoped someone would produce a ppa for.

> Running the latest firefox from firefox.com is super-duper easy...
Yes. But it's always preferable to use the package manager if possible.

> If that's challenging for you...
No. It's not in the least bit challenging. It's just a worse option than a ppa, as I pointed out above.

It's obvious now that I should have explained right at the start that I was aware of and capable of a tarball install and why I didn't want to do this unless it was the only option, and so forth, and that would have resulted in less wasted time (mine and yours). Ho hum.

---

### Post by snowpine on 2013-06-28
Hypothetically let's say there is a PPA. You would be gambling that some random volunteer is sufficiently committed to this obsolete release to check the Mozilla site on a regular basis, extract the tarball, and re-package each update into a .deb for the PPA, all in a timely manner. They would be doing exactly the same thing that you can do yourself, except that if you do it yourself, you can have complete trust in the package maintainer (you). :)

You seem to be clinging to the notion that the package manager is the only way to install software in Linux. If you want to run an end-of-life Ubuntu, you need to wean yourself off the package manager (because it points to repositories that are no longer being maintained) and learn to do your own package management. I would try to Support you, except what is the point in Supporting something that is abandoned by its own creators? Sorry you miss Gnome 2, but that is really not the fault of the volunteers on these forums. ;)

---

### Post by mikechant on 2013-06-28
> Hypothetically let's say there is a PPA. You would be gambling that some random volunteer is sufficiently committed to this obsolete release to check the Mozilla site on a regular basis, extract the tarball, and re-package each update into a .deb for the PPA, all in a timely manner.
This applies to all ppas, but people still use them. I understand the issues.


> You seem to be clinging to the notion that the package manager is the only way to install software in Linux.
No. I'm quite happy to use other methods when appropriate. I've installed from official repos, ppas, debs, tarballs of binaries and from source.

> If you want to run an end-of-life Ubuntu, you need to wean yourself off the package manager (because it points to repositories that are no longer being maintained)
As far as I can see, this does not apply in this case. I am still getting *some* updates for Lucid since the Desktop version support expired, presumably for packages that are common with the server version, which is still supported (until 2015). I've had a kernel update from the official repos in the last few weeks.

> Sorry you miss Gnome 2, but that is really not the fault of the volunteers on these forums.
I never said it was anyone's fault. I never said that there *should* be 5 years support for this particular version, just that *if* there was, many people would still be using it (I've seen many comments to this effect).
Also, I don't 'miss' Gnome 2 because I'm still running it. And I realize I can't stay on it indefinitely. I'm still evaluating MATE, Cinnamon, Gnome 3 shell, KDE and other supported alternatives. Although of course Gnome 2 *is* still supported by Red Hat/Centos etc. for about another 5 years or so.

---

### Post by mikechant on 2013-08-01
Closing thread as it's not going anywhere.

---

### Post by pqwoerituytrueiwoq on 2013-08-01
Just download firefox off the mozilla website extract to a place you have write permissions and make your shortcuts point to that firefox and it will auto update by itself like it does on windows
you can do the same thing with adobe flash by using the [FONT=courier new].mozilla/plugins/[/FONT] folder just put the .so file in there

Firefox ftp server links:
32bit:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest/linux-i686/en-US/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest/linux-i686/en-US/)
64bit:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest/linux-x86_64/en-US/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest/linux-x86_64/en-US/)

---

### Post by panorain on 2014-03-06
This tread helped me a bit as I have just installed firefox 27.0.1 on my EOL Ubuntu 10.04 computer. I extracted the new firefox.tar.bz2 package and then copied the new folder into a directory named /usr/lib/firefox 'I am not sure if that's the best place but anyways'. Then I pointed my Gnome2 launcher buttons to the new firefox.sh within the /usr/bin/firefox folder. I removed the old symlinks in the terminal and used synaptic to completely remove the firefox 20.0 from apt. P.S I probably should have done that first before transferring the new firefox version anywhere.

Then I downloaded the latest updated version of flash from the adobe website. I went into the directory /usr/lib/flashplugin-installer/ I then renamed the original libflashplayer.so to oldflashplayer.so and copied the newly downloaded libflashplayer.so into the /usr/lib/flashplugin-installer/ directory. 

Things seem to work very well.

If anyone has more input as to a better way to do this procedure or a more clean way please let us know. 

Thank you,

---


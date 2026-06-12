---
title: "After 8.04 to 10.04 upgrade, adobe problems and no sound"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by MCZ_1997 on 2010-05-04
I upgraded my system from 8.04 to 10.04.  Now I keep getting errors saying that my adobe nonfree installation is bad.  The worst part is that when I try to uninstall the Adobe package to start from scratch, it says that the problem is so bad that it can't be uninstalled, but must be re-installed.  Of course when I try to re-install it, I get errors saying it's corrupt.  I'm caught in a chicken and egg situation here.  :mad:

Also, sound no longer works on my system.  I think this is most likely a symptom of the first problem, but I'll just put it out there.

Can anybody help me.  I've read the other threads explaining how to fix this, but nothing works.

Thanks.

---

### Post by m7k on 2010-05-04
this worked for me for the flash, I had the same problem. don't know about the sound thing.

[http://ubuntuforums.org/showpost.php?p=8471230&postcount=2]("http://ubuntuforums.org/showpost.php?p=8471230&postcount=2")

---

### Post by EmilyRose on 2010-05-04
I had the same thing on my laptop (but went from 9.10-10.04), I ended up removing all the adobe files via synaptic then installing from a download and it works just fine now...

---

### Post by MCZ_1997 on 2010-05-05
m7k,

Thanks.  I tried that, but when I ran the first line of what the guy said to do, I got this:
rm: cannot remove `/var/lib/dpkg/info/adobe-flashplugin.prerm': No such file or directory

No matter what I try using Synaptic Package Manager (uninstall, or upgrade) it tells me:
E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

No matter what I do, I cannot get this thing off or upgraded.  Reinstall is grayed out, so I can't do that either.

If anybody has any other help they can offer, that would be greatly appreciated.

---

### Post by m7k on 2010-05-06
oops. obviously I had only somewhat similar problem, not the same problem. The link I posted did work for me. 

Did you try this [http://ubuntuforums.org/showpost.php?p=8194948&postcount=23]("http://ubuntuforums.org/showpost.php?p=8194948&postcount=23") or this [http://ubuntuforums.org/showthread.php?t=274844]("http://ubuntuforums.org/showthread.php?t=274844")? The first one seems to be somewhat similar with flash "Package in inconsistent state", the latter one is about forcing packet removal.

---

### Post by MCZ_1997 on 2010-05-06
m7k,

You are the man!  I guess I should call you "The Person" instead, because I don't know if you are indeed a man.  Anyhow that problem is solved.

The sound thing was stupid.  It was just that my sound was set to mute, but it's not on the system bar, so I didn't see it.

Now I'm seeing that it's taking forever to download anything.  Any ideas?

---


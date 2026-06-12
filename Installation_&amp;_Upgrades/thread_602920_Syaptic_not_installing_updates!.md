---
title: "Syaptic not installing updates!"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by old_geekster on 2007-11-04
Hey all,

I upgraded to Gutsy 64-bit using the development CD version a couple of days before the final release..  Everything was working great, including Compiz-fusion, until the latest update.  Now, "Update Manager" will download the updates, but during install it simply gets about two-thirds complete and it stops.  I have to reboot to clear the screen.

After the system reboots, I attempt to run "Update Manager" and I receive this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

So, I run 'dpkg --configure -a'  and UM runs, but it is "groundhog day" all over again.

Is anyone else having this problem?:confused:

---

### Post by Pumalite on 2007-11-04
sudo dpkg --configure -a

---

### Post by old_geekster on 2007-11-04
Thanks, Pumalite.

I did run that command.  Here is the message that I receive:

"{Setting up sun-java5-doc (1.5.0-13-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]"

I tried installing JRE 1_5_0 two days ago.  It didn't work.  So, why do I continue to receive this message?:confused:

---

### Post by Pumalite on 2007-11-04
If your Synaptic or apt-get is stuck and you can't install anything, you might need to remove that package:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by old_geekster on 2007-11-04
Okay, I finally got past that error by using "Synaptic" to do a complete uninstall of Java 1.5.  The reason I am installing Java 1.5 is "Frostwire" won't run and says that it requires JRE 1.5 or newer.  I had 1.6 installed and that didn't help.

Now, I will work on the "Synaptic" error of not fully updating.

---

### Post by old_geekster on 2007-11-04
Well, folks, I don't know what to say.  I just this minute downloaded and installed several games for my granddaughter using "Synaptic".  It worked perfectly.  Maybe, uninstalling Java 1.5 solved my problem.  It could have caused a glitch.  I will sit back for awhile to see if it is truly solved.

---


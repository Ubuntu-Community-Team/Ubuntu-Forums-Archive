---
title: "Can I install Firefox 3.0 for testing?"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2007-11-29
I want to test the new Firefox feature apng, but it is only available in the version firefox 3.0 beta.

How can I install Firefox 3.0 beta?
Can I parallel install it to my existing 2.0.0.10 ?

bye

Ronald

---

### Post by PmDematagoda on 2007-11-29
Yes you can, just the same I'm doing here:), but it seems to have messed up my old Firefox browser, so you could have some problems with your older browser.

You can install Firefox 3 using the Gutsy repositories themselves but they are not there in earlier repositories, I installed it on Gutsy that way.

---

### Post by wylfing on 2007-11-29
You could download the installer from mozilla.org and install it in /usr/local, and it should run in parallel just fine. You might run into personal profile problems, so either (a) run FF3 under a different user or (b) back up your profile (the ~/.mozilla directory) before experimenting with FF3.

If you do install under /usr/local, you're probably going to want to mirror all your plugins, so don't forget to make links or copy over all the .so files from the "real" FF install.

---

### Post by ELMIT on 2007-11-29
I have downloaded:

firefox-3.0b2pre.en-US.linux-i686.tar.bz2

opened the directory, but have no clue how to use it now.

Some tries:
ronald@ronald-desktop:~/Desktop/downloads/firefox$ ./firefox-bin
./firefox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

./firefox   opens 2.0.0.10

ronald@ronald-desktop:~/Desktop/downloads/firefox$ ./run-mozilla.sh 

run-mozilla.sh: Cannot execute .

ronald@ronald-desktop:~/Desktop/downloads/firefox$ sh run-mozilla.sh 

run-mozilla.sh: Cannot execute .

ronald@ronald-desktop:~/Desktop/downloads/firefox$ ./updater 
Usage: updater <dir-path> <parent-pid> [working-dir callback args...]


How can I install it (safe & parallel to 2.0.0.10) ???


bye

Ronald

---

### Post by PmDematagoda on 2007-11-29
Did you try installing Firefox 3 as I gave in my first post ELMIT? It would be very much easier than the way you are trying to install Firefox.

---

### Post by ELMIT on 2007-11-29
something gone wrong!

I installed with synaptic and when I restart Firefox it is still 2.0.0.10

I copied before ~/.mozilla to .mozilla-firefox-2.0.0.10


What can I try next?

---

### Post by ELMIT on 2007-11-29
found it:

/usr/local/bin/firefox-3.0   and not the old version /usr/local/bin/firefox

Thanks!

bye

Ronald

---

### Post by ELMIT on 2007-11-29
Going to Yahoo mail:

Caution: rough seas ahead. You appear to be using an older version of Firefox.
The all-new Yahoo! Mail works best with Firefox 1.5.0.2 or higher. You can upgrade, continue at your own risk, or simply go to Yahoo! Mail Classic.


-- it is not the only thing (recently) that makes me wonder of the qs of yahoo, ....

---


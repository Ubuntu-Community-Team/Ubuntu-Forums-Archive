---
title: "Just upgraded to Ubuntu 18.10 and it broke BOINC"
date: 2018-10-18
forum: Installation &amp; Upgrades
---

### Post by Keith Myers on 2018-10-18
I'm in trouble now with the upgrade to Ubuntu 18.10.  It removed libcurl3 that is a required dependency by boinc manager.

I was able to install libcurl3 alongside libcurl4 with no issue with Ubuntu 18.04.  When I attempt to reinstall libcurl3 in 18.10 I get told that libcurl3 has been obsoleted and replaced by libcurl4.

What do I have to do to get BOINC running again?  This is a urgent matter.  All help is appreciated.:(

---

### Post by Claus7 on 2018-10-19
Hello,

this is not a solution you are seeking, yet if you are in a hurry, you might find this useful adjusted to your needs:
[https://askubuntu.com/questions/1030479/ubuntu-18-04-unable-to-install-viber](https://askubuntu.com/questions/1030479/ubuntu-18-04-unable-to-install-viber)

Regards!

---

### Post by ejbiow on 2018-10-19
Not helpful, perhaps, but I just upgraded from bionic to cosmic and boinc seems to have survived. Now if I can just figure out why I couldn't upgrade samba without stripping it out...

---

### Post by Keith Myers on 2018-10-19
After having posted for help in the BOINC forums, I have learned that after BOINC 7.9.3, that libcurl4 has replaced libcurl3 in all the previous versions.  I run Seti@Home user versions 7.4.44 and 7.8.3 which depend on libcurl3.  There are some operational benefits to running the user versions over any repository version.  So either switch to a recent repository version, stick with 18.04 or install a different curl that I have discovered that allows curl3 and curl4 to coexist.  That will be the option I will pursue later today on a test partition with 18.10.

---

### Post by Kurt_Alan on 2018-10-20
I am loving 18.10 But it broke BOINC for me too. It worked briefly, then failed. Repeated purges and reinstalls failed.
My workaround: I am running 18.04 Ubuntu MATE in vmware player -- no issues. I allotted 5GB of RAM. I have 16 GB. Toggling between the OS's is a snap (!). 

MATE fails Dropbox, another critical program for me. Now, with two simultaneous OS's running seamlessly, I have the best of both worlds. I know this is a work-around and not the solution you wish.

---

### Post by Keith Myers on 2018-11-27
You can get older versions of BOINC to run on 18.10 IF you get the libcurl34 ppa added to your repositories.  Install the libcurl4 version from that ppa and it allows both libcurl3 and libcurl4 to co-exist with each other.  BOINC and other programs that depend on libcurl3 are happy again.

---


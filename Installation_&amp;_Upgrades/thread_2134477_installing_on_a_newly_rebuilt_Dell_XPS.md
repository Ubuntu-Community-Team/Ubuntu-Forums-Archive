---
title: "installing on a newly rebuilt Dell XPS"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by mikebail on 2013-04-11
Ok guys so the specs are
2 gig ram
3.2 GBPs Pentium 4
120 gb HDD





So here`s what happened


It started to boot, I know this from sounds.
5 minutes later I got this screen 


[img]http://img145.imageshack.us/img145/360/84826257.jpg[/img]


Then it sits on this screen for a good 3 minutes.


I then get an error 
```

[     93.580828]  Kernel panic - not syncing: Attempting to kill init! exit code=0x00000100
[     93.580828]
[     93.580828]  Pid: 1, comm: run-init Not tainted 3.5.0-23-generic #35~precise1-Ubuntu
[     93.580828]    Call Trace:
[     93.580828]    [<c15cd72b>] panic+0x81/0x89
[     93.580828]    [<c104a0ac>] find_new_reaper+0xfc/0x100
[     93.580828]    [<c104b474>] forget_original_parent+0x34/0x170
[     93.580828]    [<c10fcd30>] ? perf_cgroup_switching=0x180/0x180
[     93.580828]    [<c104b5c3>] exit_notify+0x13/0x100
[     93.580828]    [<c104bd63>] do_exit+0x1b3/0x3f0
[     93.580828]    [<c137dfc0>] ? tty_write+0x220/0x220
[     93.580828]    [<c104c0b8>] sys_exit+0x18/0x20
[     93.580828]    [<c15e2da4>] syscall_call+0x7/0xb
[     93.580828]  panic occurred, switching back to text console

```


Any one got any ideas, also I cant type commands.


Thanks in advance,
Mikebail

---

### Post by ajgreeny on 2013-04-11
I assume this is 12.10, so will be using the PAE kernel, and as far as I'm aware, a P4 is OK running a PAE kernel, so the next question is 
what graphic card?
and did you check the md5sum of the .iso file you burned to CD/DVD or USB against those listed at [https://help.ubuntu.com/community/UbuntuHashes?](https://help.ubuntu.com/community/UbuntuHashes?)

---

### Post by mikebail on 2013-04-11
I believe it`s 12.04.

---

### Post by mikebail on 2013-04-11
its an amd thats all I know lol OLD computer XD

---

### Post by mörgæs on 2013-04-11
The kernel 3.5.0-23 indicates 12.04.2 

If we are dealing with old stuff you should consider L/Xubuntu 12.10 in stead of Ubuntu.

---

### Post by mikebail on 2013-04-11
ok il give that a try :D

---

### Post by Zestypanda on 2013-04-11
> **mikebail said:**
> its an amd thats all I know lol OLD computer XDI'm confused, you say it's pentum 4 in the beginning then say its AMD if its a P4 then it can't run the AMDX64 version of Ubuntu, you will have to download the X86INTEL version, but if it IS an AMD chip then why did you say it was INTEL in the beginning?

---

### Post by MAFoElffen on 2013-04-11
Questions:
- What model number XPS?
- What Arch 12.04 iso are you trying to run? (i386 or amd_64)

---

### Post by MAFoElffen on 2013-04-11
> **Zestypanda said:**
> I'm confused, you say it's pentum 4 in the beginning then say its AMD if its a P4 then it can't run the AMDX64 version of Ubuntu, you will have to download the X86INTEL version, but if it IS an AMD chip then why did you say it was INTEL in the beginning?
Early XPS'es had Pentium P4's and came with ATI Radeon Graphics. Some early boards, even though the P4 was 64bit, but some of the early memory controllers on those early boards, addressing memory... So finding out which model of XPS would be helpful.

EDIT--
If it were me, on any Ubuntu flavored distro with that error... 
First, test the ISO for errors and that it was burnt correctly ("Test Disk"). Then test memory.

Then reboot and... > At the first panel with the keyboard/person icon. hit <Esc> > hit F6 at the advanced install menu > hit <Esc>... Edit the boot line to remove/replace the text "quiet splash vt.handoff=7" with "--verbose single". Hit <F10> to boot... and see if it will boot the kernel itself.

Those options should turn on verbose kernel boot messaging, display them to the screen and boot to a tty single user console. If it does get to that point, then it's further on in higher layers. In it doesn't get to that point and gets kernel-panic, then you need to try a different kernel arch or flavor. Your options for that are the amd_64 ISO, the i386 ISO... or the non-pae net-install ISO.

---

### Post by mikebail on 2013-04-11
ok i did a test and there was errors in 14 files... what do I do now?

---

### Post by mikebail on 2013-04-11
ok i did a test and there was errors in 14 files... what do I do now? oh and its a dell - dimension XPS Gen 2 Series

---

### Post by mörgæs on 2013-04-12
You mean tested the ISO? 
If it has errors just download a new one.

---

### Post by ajgreeny on 2013-04-12
> **mörgæs said:**
> You mean tested the ISO? 
If it has errors just download a new one.
And to make it more likely to download successfully, use a torrent client.  If there are any corrupt packets in the ISO file the torrent will download them again and replace the dodgy parts,

Then if you are burning to CD, do it as slowly as your drive will let you.

---

### Post by MAFoElffen on 2013-04-12
Status- He' s been skype'ing with me. Yes he had a bad Disk. Did not test well and had errors. He has an old XPS Gen2.

I have him Download a new Unbuntu 12.04 32bit iso. I walked him through burning the ISO. He didn't know (yet) to burn at lowest speed. I walked him though custom booting the iso to try to boot the LiveCD "try" into  a single user tty console just to see if he could boot a 32bit kernel. A no-go.

I had him the dl link to the 12.04 non-PAE net-install iso. He did dl'ed itthat last night and is supposed to connect back with me tonight when he gets home... I gave him some quick tips last night about how the net-install disk works, in case he wnted to tackle that on his own... But it sounded like he will feel better with being "guided."

He just messaged me he's busy with family. His words"so no Linux.." (at moment...)

---

### Post by mörgæs on 2013-04-12
Thanks for your effort.

Wouldn't it be the easiest to install Xubuntu 12.04.2? Two years of support from today on non-PAE processors.

---


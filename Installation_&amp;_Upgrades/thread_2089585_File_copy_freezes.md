---
title: "File copy freezes"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by Paul A C on 2012-11-29
I have just installed Lubuntu 12.10 on an old NEC Powermate.

The issue I have is I cannot copy files over the Network to either of my hard disks in the machine.  The first file (or 2) copy, then the copying freezes.  I have tried the following:-

I am copying from another Lubuntu PC here is a summary of what does and does not work:-
1.)Using PCManFm to  sda3 (Reiser) Fail (File 1 14K)
2.)Using PCManFm to sda2 (ext4) Fail (File 1 0bytes )
3.)One file at a time Pass Reiser OK  ext4 OK
4.)Using Nautilus to Reiser Fail 15 files created, some 0 bytes
5.)Using Nautilus to Ext4 Fail 9 files created, some 0 bytes
6.)From USB to Reiser OK almost instant
7.)Replace Network card (3Com) with NE2000 Compatible still fails after 1 file.
8.)Using CP command from terminal. Same error, hangs during second file
9.) copy **to** this PC from the other PC Pass, works just fine.
The fact that the USB copy works 'seems' to indicate a Network issue, but I downloaded updates all OK, and I have used BBC Iplayer to view/listen, and as test 9 above shows, I can copy to the PC from another one, it is only copying from another PC to this one that does not work!  I guess that is a work-around of sorts, but hardldy satisfactory.

My next test is to install Lubuntu 12.04 on this box, which I have working fine elsewhere. 

Not seen this problem on any posts despite quite a wide search: anyone any ideas?

Installation of Lubuntu 12.04 completed quicker than expected.  Filecopy using PCManFM (default file manager) worked perfectly.  Looks like a 12.10 specific issue.

---


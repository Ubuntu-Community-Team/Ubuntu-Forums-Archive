---
title: "Fatal Error during GRUB install"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by snackzilla on 2005-06-26
Just tried to install Ubuntu today. When the install got to installing GRUB to the MBR, it stopped, saying a fatal error has occured. My only guess is that b/c I use a Sony, the computer is set up so the first gig or so on the hard drive is a recovery partition and GRUB is trying to write to it. If memory serves, the error is saying that a fatal error occured while "Installing GRUB (hd0) "; the error message doesn't say anything else. 

I tried using LILO, but that failed as well.

Has this happened to anybody before? Any suggestions? Thanks in Advance!

---

### Post by mingus on 2005-06-26
Is W$ installed on this machine?  Or do you have a drive overlay installed?

Grub is not trying to install to the first partition, but rather the Master Boot Record.  However, if that partition is "hidden", that might create a problem.  When you installed Ubuntu, how did you set up the partitions?

And grub can be installed elsewhere, but we'll need the above info before advising.

---

### Post by masonmop on 2005-06-27
[QUOTE=snackzilla]Just tried to install Ubuntu today. When the install got to installing GRUB to the MBR, it stopped, saying a fatal error has occured. My only guess is that b/c I use a Sony, the computer is set up so the first gig or so on the hard drive is a recovery partition and GRUB is trying to write to it. If memory serves, the error is saying that a fatal error occured while "Installing GRUB (hd0) "; the error message doesn't say anything else. 

I tried using LILO, but that failed as well.

Has this happened to anybody before? Any suggestions? Thanks in Advance![/QUOTE]
 That happened to me the first time I tried to install Ubuntu. The second, third and fourth times it installed fine, but it still would boot windows automatically.

---

### Post by mingus on 2005-06-27
[QUOTE=masonmop]. . . but it still would boot windows automatically.[/QUOTE]

post not very clear . . . so is there still a problem?

---

### Post by Hugh Jass on 2005-06-27
I experienced the same problem, having a fatal error during GRUB Install. LILO installed, but without the boot loader it just boots into Windows.

I do not have any drive overlay installed. In fact, the only thing on the machine is Win XP Pro, replete with updates. It's a VAIO PIII.

I have a 40 gb disk clipped at 32 gb, partitioned into a 10 gb drive and a 22 gb drive. Windows is installed on the 10gb drive. I formatted the 22gb drive into ext3 and installed Ubuntu on it. Everything went off without a hitch (congrats!) except for GRUB. 

Is that enough information to get started? Thank you for your time and help.

---

### Post by mingus on 2005-06-27
who's on first here???  snackzilla or masonmop or Hugo Jass . . . confusing . . . pls, each user create his/her own problem thread

---

### Post by masonmop on 2005-06-28
[QUOTE=mingus]who's on first here???  snackzilla or masonmop or Hugo Jass . . . confusing . . . pls, each user create his/her own problem thread[/QUOTE]
I made my own [thread](http://ubuntuforums.org/showthread.php?t=44642) a couple of days ago.

---


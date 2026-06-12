---
title: "apt-cacher very slow"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by Gadgetman on 2011-07-24
Ubuntu 11.04 AMD64

apt-cacher is very slow. if I do an apt-update, it runs at a snails pace.

If I alter my sources.list to bypass apt-cacher and the do an apt-get update - it is very FAST!!. 

These tests are being done on the server that has the apt-cacher installed. I did try the same test on another ubuntu 11.04 PC (on the same 1G LAN) to this server's apt-cacher - same result.

Typical sources.list entry is...
deb [http://10.1.5.30/apt-cacher/security.ubuntu.com/ubuntu/](http://10.1.5.30/apt-cacher/security.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse

(where 10.1.5.30 is the apt-cacher server)

Had upgraded from 10.10 to 11.04 (not sure if this is relevant)

---

### Post by yusuf.hm on 2011-08-06
I have the same issue; have you found a solution in the meantime?

---

### Post by Gadgetman on 2011-08-08
No not yet!!
I have looked at the apt-cacher log (/var/log/apt-cacher/error.log) and find the following entries which might be a clue to the problem...appears to be a missing header file?

Compilation failed in require at /usr/share/apt-cacher/apt-cacher.pl line 9, <GEN3> line 11.
Mon Aug  8 13:56:40 2011|error [912]: sys/syscall.ph is missing, see the h2ph man page at /usr/share/apt-cacher/apt-cacher line 1379
Compilation failed in require at /usr/share/apt-cacher/apt-cacher.pl line 9, <GEN1> line 9.
Mon Aug  8 13:57:03 2011|info [757]: return_file /var/cache/apt-cacher/packages/security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources.gz aborted by timeout at 0 of  bytes
Mon Aug  8 14:14:43 2011|error [4704]: sys/syscall.ph is missing, see the h2ph man page at /usr/share/apt-cacher/apt-cacher line 1379

---

### Post by yusuf.hm on 2011-08-08
Based on that log, it seems to be similar to an old bug with Perl:
[https://bugs.launchpad.net/ubuntu/+source/perl/+bug/315991](https://bugs.launchpad.net/ubuntu/+source/perl/+bug/315991)

And when I try the command they gave there, I get the same error message:

```
yusuf@home-desktop:~$ perl -e "use Filesys::DiskSpace; warn df('/');"
sys/syscall.ph is missing, see the h2ph man page at -e line 1
```

---

### Post by Gadgetman on 2011-08-09
SOLVED!!

Thanks yusuf.hm for your input which got me investigating further...

I found that

```
# perl -e "require 'sys/syscall.ph';"
Can't locate asm/unistd.ph in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/sys/syscall.ph line 7.
Compilation failed in require at -e line 1.
```

indicating that asm/unistd.ph is missing.
On another "clean Ubuntu 11.04 installation I did a locate for unistd.ph and found..

```
# locate unistd.ph
/usr/lib/perl/5.10.1/asm/unistd.ph

```

On my broken Ubuntu 11.04 this folder (/usr/lib/perl/5.10.1/asm)is missing!! I copied the complete /usr/lib/perl/5.10.1/asm folder to my broken ubuntu 11.04 PC and voila it works!!

```
root@MalutiDVR:~# perl -e "require 'sys/syscall.ph';"
root@MalutiDVR:~#

```

Now my apt-cacher runs fast!!
:)

---

### Post by yusuf.hm on 2011-08-09
Oh that's nice; you gave me yet another idea.

I'll try locating that file on my current installation; maybe it's there but just misplaced.

I'll post back in the afternoon when I get home.

EDIT: I was able to check my PC remotely, and indeed the folder is missing; I wonder how I can get it back (I'll try uninstalling and re-installing Perl).

EDIT again: Uninstalling Perl seems a bad idea since a lot of other modules want to go away with it :(. Guess I'll just have to install on a VM and take the files...

---

### Post by yusuf.hm on 2011-08-10
I finally did like you, copied the files, and my apt-cacher is finally working!!

I have attached a compressed file of the asm folder here, in case somebody else has the same problem but no way of getting a clean installation.

Just unzip the file in /usr/lib/perl/5.10.1/ and you're good to go.

Just a little piece of info: I'm using 64-bit, I don't if it'll work on 32-bit.

---

### Post by maurograca on 2011-08-12
Exactly the same. After upgrading Ubuntu messed all...

Thanks for solution.

---

### Post by davidmcq on 2012-05-15
excellent help - thanks...

how do I get this into the package manager so that it doesn't happen again next time?

---

### Post by Gadgetman on 2012-05-16
Hi davidmcq,
What I found is that once you have performed the "fix" it doesnt disappear on subsequent apt-get updates/upgrades.

This problem is not in the later releases of ubuntu.

---


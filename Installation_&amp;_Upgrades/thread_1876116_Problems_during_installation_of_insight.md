---
title: "Problems during installation of insight"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by Studiologe on 2011-11-05
Hello tgether,
I'm quite new to the Linux community and I was hoping to get some support from the experts with the installation of insight.
The reason is that I'm actually reading Jeff Duntemanns "Assembly language step by step" and he is heavily using this tool.
I already googled and found his commentary on the pitty of insight being removed from the repository, but I couldn't find any help / support on how to get it to work on my system.

I'm running (a distro of) Ubuntu lucid 

If I try to install insight make failed with
cc1: warnings being treated as errors
linux-nat.c: In function ‘linux_nat_info_proc_cmd’:
linux-nat.c:2879: error: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
make[2]: *** [linux-nat.o] Error 1
make[2]: Leaving directory `/home/stud/media/software/insight-6.8-1/gdb'
make[1]: *** [all-gdb] Error 2
make[1]: Leaving directory `/home/stud/media/software/insight-6.8-1'
make: *** [all] Error 2


And I was wondering if anybody would be willing to help me on this problem?
I attached the whole log of output when running 
./configure    as well as
make

Please somebody help me and let me know what is roooong :-) with my set-up.

Thanks,
Stud

---

### Post by Studiologe on 2011-11-06
No ideas folks?
I really got into a dead-end here and need some Guru-help.
Please advise if you have any ideas, or need more input to help me with this!

Thanks

---

### Post by notgary on 2012-09-08
I know this thread is old, but I found it via Google and other's will do likewise, so having an answer on it would be helpful.

The problem is that Insight's build system is configured to treat warnings as errors, as you can tell from the first line of the error message you posted. All you need to do to is this is to disable that particular feature using

```
./configure --disable-werror
make
sudo make install
```

---


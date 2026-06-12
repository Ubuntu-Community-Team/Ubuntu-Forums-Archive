---
title: "Package Manager Problem - language-pack-en-base error"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by gfk on 2007-07-13
Hi,

I'm having troubles with the package manager, apt-get and aptitude cannot open the file lists for the package 'language-pack-en-base'.  It states a input/output error, whatever that means.


heres the error output I get when I try to do install or remove programs through aptitude ot apt-get.

(Reading database ... dpkg: error processing bonnie++ (--remove):
 unable to open files list file for package `language-pack-en-base': Input/output error
Errors were encountered while processing:
 bonnie++
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


I looked through here and searched through google but nothing has worked or have been relevant to my problem.

I'm thinking of using "sudo aptitude --purge language-pack-en-base" then removing the package and try to install it again with a .deb I have.
Do you think that would be wise to do so?

Thanks
Shaun

**update**
It became apparent that I had some bad sectors on my hard drive which fsck noticed when it was scheduled to check during boot time and removed loads of corrupted files.
Now aptitude works again and I reinstalled the language-pack-en-base just in case.
Hopefully my install is still in good condition after my deleting session I was quite sure what it did.

---


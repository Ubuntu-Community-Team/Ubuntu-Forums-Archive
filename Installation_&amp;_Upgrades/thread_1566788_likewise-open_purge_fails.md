---
title: "likewise-open purge fails"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by huuan on 2010-09-02
Initial install of likewise failed as it had a conflict with winbind so I purged winbind. Next I installed likewise OK but on attempting to join the domain I got error:

Error: Unable to parse krb5.conf [code 0x00080040]

The krb5.conf file on your system (located in either /etc/krb5.conf or
/etc/krb5/krb5.conf) could not be parsed. Please send the file to Likewise
technical support.


I had already been using  kerberos so I tried over after putting loose permissions 0666 on /etc/krb5.conf but same result.
 
Don't have time to enter into a technical discussion with the likewise folks so I decided to uninstall likewise-open

Well it will not uninstall (arrrgh!) gives the error:
Writing extended state information... Done
(Reading database ... 43634 files and directories currently installed.)
Removing likewise-open ...
dpkg: error processing likewise-open (--purge):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 likewise-open
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

and even after reboot will not purge.

I see a bug https://launchpad.net/bugs/230466 which is related but was fixed years ago.

Any idea what I can do to purge likewise from my system short of reinstalling everything except likewise?

Thanks.

---

### Post by llawwehttam on 2010-09-02
Could you run the following?

```
sudo apt-get clean ; sudo apt-get autoclean ; sudo apt-get check
```

and post the output.

---

### Post by huuan on 2010-09-02
```
sudo apt-get clean ; sudo apt-get autoclean ; sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

thanks.

BTW I should have said: running 10.04 LTS server 64-bit

---

### Post by huuan on 2010-09-03
solved:
 at this stage a re-install pf the entire system (about 2 hours) will be faster than trying to get support for what is likely an isolated problem.
Thanks all. ):P

---

### Post by Obfuscator on 2011-02-13
The same happened to me, turned out to be a non-purged sshd config which confused the prerm-script, see [https://bugs.launchpad.net/ubuntu/+source/likewise-open5/+bug/452228?comments=all](https://bugs.launchpad.net/ubuntu/+source/likewise-open5/+bug/452228?comments=all)

Renaming the sshd_config file fixed the problem.

---


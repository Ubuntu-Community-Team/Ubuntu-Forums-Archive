---
title: "vmware install failed"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by underdog512 on 2006-07-10
I recently tried to install Vmware Server.  However, it does't seem that the installation is completing. here is the output I am getting:


Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin] /home/amobley/vmware

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/home/amobley/sbin]

The path "/home/amobley/sbin" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the library files?
[/home/amobley/lib/vmware]

The path "/home/amobley/lib/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the manual files?
[/home/amobley/man]

The path "/home/amobley/man" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/home/amobley/doc/vmware]

The path "/home/amobley/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

---

### Post by srichter on 2006-07-16
Hi,

I would like to use vmware server too.

But i'm getting exactly the same error like underdog512...


Any ideas to fix it? 
Or, underdog512, are you still getting this error message?
Or did you solve it?


please help me ( us ) ..

greetings, srichter

---

### Post by syawillim on 2006-08-19
Once you unpack the downloaded tarball you need to edit ```
vmware-install.pl
```.

Repalce:
```
install_dir( './vmware-vix/bin' , $rootdir . '/bin/', \%patch);
```

With:
```
install_dir( './bin' , $rootdir . '/bin/', \%patch);
```

Also select the default for the following:
```
In which directory do you want to install the binary files?
[/usr/bin]
```

Specify the locations of your virtual machines directory, this comes near the end of the process.

---

### Post by stephensheppard on 2006-08-27
Thanks syawillim! This fixed the problem and I was able to install VMware server. Now to try to get XP to run.

---

### Post by theartofbone on 2007-12-29
woohooo, I was having the same exact problem these guys were having and followed the instructions posted by syawillim and it worked like a charm... now, the question is, what now? lol... Guess Ill figure it out. THanks guys

---


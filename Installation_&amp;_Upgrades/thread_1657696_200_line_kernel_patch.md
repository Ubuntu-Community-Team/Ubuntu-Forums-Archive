---
title: "200 line kernel patch"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by LinuxIsAmazing on 2011-01-01
I am currently using Ubuntu 10.04.  How would I install the 200 line kernel patch?  The one that is supposed to make your computer so much faster.  I would appreciate everyone's help.  Thank you very much.

---

### Post by |{urse on 2011-01-01
[http://www.howtoforge.com/kernel_compilation_ubuntu?&](http://www.howtoforge.com/kernel_compilation_ubuntu?&)

This is the guide I used last.

---

### Post by lithopsian on 2011-01-01
The patch won't make your computer faster, in fact it will make it marginally slower.  It will make the response of your desktop better when the CPU is maxed out.  If you run with your CPU maxed much of the time out then this could be considered essential.  At other times you may get a snappier response to actions on the desktop of foreground application.  Or not, depending on your hardware.

There are Ubuntu kernel debs out there already with the patch that you might want to try first.  Or if you want to compile a kernel anyway then give it a go.  It isn't hard, just a little time-consuming.  Download source, untar in /usr/src, and make.  In your case, apply patch before you make.  In most cases you would do well to start with a kernel config copied from your existing kernel.  After you get that working you can spend many happy days reconfiguring the kernel to better match your hardware and software needs.

You can achieve the same results, possibly better if you tune it for your exact conditions, by manually setting up cgroups on your system.  These are enabled in most kernels but not often used on desktops.  Against, it is just a way of letting your interactive desktop processes get better response at the expense of whatever is chewing up your CPU.

---

### Post by TenPlus1 on 2011-01-01
Phoronix recently published an article regarding a ~200 lines Linux Kernel patch that improves responsiveness under system strain. Well, Lennart Poettering, a RedHat developer replied to Linus Torvalds on a maling list with an alternative to this patch that does the same thing yet all you have to do is run 2 commands and paste 4 lines in your ~/.bashrc file. I know it sounds unbelievable, but apparently someone even ran some tests which prove that Lennart's solution works. Read on!

Basically, Lennart explains you have to add this to your ~/.bashrc file (important: this won't work on Ubuntu. See instructions for Ubuntu further down the post!):

   if [ "$PS1" ] ; then  
           mkdir -m 0700 /sys/fs/cgroup/cpu/user/$$
           echo $$ > /sys/fs/cgroup/cpu/user/$$/tasks
   fi

And run the following commands as super user:

mount -t cgroup cgroup /sys/fs/cgroup/cpu -o cpu
mkdir -m 0777 /sys/fs/cgroup/cpu/user

Further more, a reply to Lennart's email states that his approach is actually better then the actual Kernel patch:


--- UBUNTU INSTRUCTIONS HERE ---


Start by editing your rc.local file, running sudo gedit /etc/rc.local and add the following lines above "exit 0":

mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

Save and exit gedit. Now, make it executable:

sudo chmod +x /etc/rc.local

After doing this, edit the .bashrc file found in your home directory (gedit ~/.bashrc) and, at the end of this file, add:

if [ "$PS1" ] ; then  
   mkdir -m 0700 /dev/cgroup/cpu/user/$$
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi

One last thing. To make sure that cgroups are deleted whenever the last task leaves, run:

sudo gedit /usr/local/sbin/cgroup_clean

And copy-paste this:

#!/bin/sh
rmdir /dev/cgroup/cpu/$*

Once again, save the file, exit gedit and make it executable:

sudo chmod +x /usr/local/sbin/cgroup_clean

Done! Restart your computer to apply the changes.

---

### Post by mörgæs on 2011-01-01
Thanks for the bashrc-idea.

Is it correct that the kernel patch is to late for 11.04, but it will be standard in 11.10?

---

### Post by afrodeity on 2012-03-27
Wondering whether one should remove the patch if upgrade to Oneiric or Plunky Poodle?

---

### Post by mörgæs on 2012-03-27
Why do you want to remove it?

---

### Post by afrodeity on 2012-03-29
I am experiencing slow programme startup since I upgraded and wondering if there is interaction going on between the patch and the newer kernel?

---

### Post by mörgæs on 2012-03-29
It's not really a patch any more but an integrated part of the new kernels. 

There are lots of possible reasons for a slow start-up. Best to do some more analysing before trying to solve the problem.

Does **top** or **gkrellm** tell you anything about the processor load? Is it kernel load or load in userland?

---


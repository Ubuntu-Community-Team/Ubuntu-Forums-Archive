---
title: "can't install selinux-policy-default"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by na3po4 on 2007-04-02
I am answering my own question here. I thought I would post the answer to help someone else in the future.

Original problem was that I needed to update my subversion.  I checked the forums and found this post [http://www.ubuntuforums.org/showthread.php?t=379825&highlight=subversion]("http://www.ubuntuforums.org/showthread.php?t=379825&highlight=subversion"). It all went well until the part where it needed selinux.

Solution:

You need to enable selinux in your kernel at boot.  Edit /boot/grub/menu.lst, find your default kernel and add the following lines 

Mine looks like this after the change (my bolding):

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash **selinux=1 enforcing=0**
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

Next, reboot. Ensuring you boot off the changed kernel.

The next part took a while to find. When I tried to install selinux-policy-default, I got this error

Compiling policy ...
/usr/bin/checkpolicy:  loading policy configuration from policy.conf
/usr/bin/checkpolicy:  policy configuration loaded
/usr/bin/checkpolicy:  writing binary representation (version 20) to /etc/selinux/./policy/policy.20
Building file contexts files...
Validating file contexts files ...
Installing file contexts files...
  File "/usr/sbin/genhomedircon", line 35
    except:
         ^
SyntaxError: invalid syntax
make: *** [/etc/selinux/./contexts/files/file_contexts] Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 selinux-policy-default
E: Sub-process /usr/bin/dpkg returned an error code (1)

The answer is found here: [ http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=369852]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=369852")

Edit /usr/sbin/genhomedircon and add the required formatting.

I was able to successfully re run apt-get install selinux-policy-default after I made the change to /usr/sbin/genhomedircon

Thanks, hope it helps

---


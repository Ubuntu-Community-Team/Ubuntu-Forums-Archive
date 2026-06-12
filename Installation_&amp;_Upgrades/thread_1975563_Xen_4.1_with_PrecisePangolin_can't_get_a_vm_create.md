---
title: "Xen 4.1 with PrecisePangolin: can't get a vm created/running"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2012-05-07
I'm brand new to Xen and am trying to get anything to work correctly.

I have installed PrecisePangolin in a volume.
Then installed Xen via
  sudo apt-get install xen-hypervisor-4.1-amd64

and then installed the xen-tools via:
    sudo apt-get install xen-tools

xen-tools is not aware of PrecisePangolin (nor Oneiric), so I 
had to do this:
  cd /usr/share/doc/xen-tools
    sudo ln -s karmic.d precise.d

Although the doc says `xm` is deprecated, I had to explicitly
tell the xen-tools to use `xl` via:
  sudo vi /etc/default/xen
    Change:
        TOOLSTACK=
        to:
        TOOLSTACK=xl

I also had to uncomment a line to get past a bridge error:
sudo vi /etc/xen/xend-config.sxp
    Uncomment this line:
        (network-script network-bridge)


I then try to create a machine, xen002, via:

sudo xen-create-image \
--fs=ext3 \
--image=full \
--memory=1Gb \
--size=20Gb \
--swap=2Gb \
--install-method=debootstrap \
--arch=amd64 \
--dist=precise \
--lvm=vg1 \
--hostname=xen002 \
--dhcp \
--vcpus=1 \
--verbose


This command finishes with these last few lines:

...
Done
Setting up root password
Generating a password for the new guest.
All done           <-- at this point the install is 99.99% done.
Executing : umount /tmp/768v5AaDGF/proc
Finished : umount /tmp/768v5AaDGF/proc 2>&1
Unmounting : /tmp/768v5AaDGF/dev/pts
Executing : umount /tmp/768v5AaDGF/dev/pts
Finished : umount /tmp/768v5AaDGF/dev/pts 2>&1
Unmounting : /tmp/768v5AaDGF
Executing : umount /tmp/768v5AaDGF
umount: /tmp/768v5AaDGF: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
Finished : umount /tmp/768v5AaDGF 2>&1
Running command 'umount /tmp/768v5AaDGF 2>&1' failed with exit code 256.
Aborting
See /var/log/xen-tools/xen002.log for details
cannot remove directory for /tmp/768v5AaDGF: Device or resource busy at /usr/share/perl/5.14/File/Temp.pm line 902


I've discovered that there is a `sshd` process running that still
has a hold on some files that were in the /tmp/768v5AaDGF
directory.
If I kill the `sshd` process, I can then manually do this:
     sudo umount /tmp/v768v5AaDGF


I can also successfully create/start/run the new xen0002 vm, via:
  $ sudo xl create /etc/xen/xen002.cfg
      Parsing config file /etc/xen/xen002.cfg
      Daemon running with PID 17949
  $


At this point, is the xen002 machine actually running?


I try to "connect" to xen002, via:

    sudo xl console xen002

<deleted a bunch of stuff>
...
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) 


So "connecting" to the machine seems to fail with
many messages all relating to a bunch of stuff missing.


(By looking at the output, it appears that it's trying to
 start the machine in addition to connecting. I thought
 the machine was already "running".
 )

Anyways, I notice (after rebooting), that i have a mounted volume
that I can access under /media/3c4e8dcd-6d08-44fd-a8b1-18071eb73613
I don't see any directories nor files under this.
Shouldn't I see the directory heirarchy of an actual machine?

While the "xen-create-image" was running, I was monitoring the
/tmp/v768v5AaDGF directory where the new machine was "temporarily"
being created. At one time, there were 53204 files in it with
directories such as:
bin  boot  dev	etc  home  lib	lib64  lost+found  media  mnt  opt  proc  root	run  sbin  selinux  srv  sys  tmp  usr	var

So it was progressing well in my eyes, but then these directories/files
never made it to the mounted volume.

Anyone have any ideas to make any of this work?

Has anyone in the world got this exact setup to work?
(Did you have to make the same edits I did in the beginning?)

I've spent many days redoing and undoing and rebooting and reading
documentation and reading some of the pertinent scripts, and it's 
still all very murky to me.

---

### Post by gmoore777 on 2012-05-08
The short story on how to fix my dilemna was to edit:
   /usr/lib/xen-tools/karmic.d/70-install-ssh

And to add code to shut down the sshd process that was just started
after installing the openssh-server package:
        chroot ${prefix} /usr/sbin/service ssh stop

Longer story:
The xen-create-image perl script has the intention of preventing the sshd
process from starting up, but it's not working. I don't really know why.

Because this sshd binary starts up upon the installation of the
openssh-server package and loads up other libraries, the
clean up "END" subroutine in xen-create-image fails while unmounting
the /tmp/<tempname> directory.
That failed unmounting is not fatal. 
The new machine is still intact at that moment.
But when the perl script, xen-create-image, exits, any temporary
directory location as created by the File::Temp Perl class gets
removed automajically. 
The /tmp/<tempname> directory was created via this File::Temp Perl class
and will get removed. Unfortunately it's not the empty directory
as it should be after successful unmounting, it's the entire new machine
file heararchy since the unmounting failed.
Thus after xen-create-image, when one tries to list out the contents
of the root of the new machine, for me it would be at the top of my
volume, I see no directories, no files. Nothing.

I will log a bug against the xen-tools package as that is where the
file /usr/lib/xen-tools/karmic.d/70-install-ssh is installed from.

---

### Post by gmoore777 on 2012-05-08
Just submitted this bug against xen-tools:
[https://bugs.launchpad.net/ubuntu/+source/xen-tools/+bug/996789](https://bugs.launchpad.net/ubuntu/+source/xen-tools/+bug/996789)

---


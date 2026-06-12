---
title: "HOW TO:  install Lucid/10.04 LTS on Xen 3.1 with xen-tools/debootstrap"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by ac4000 on 2010-05-12
Following are the steps I took to install Lucid on Xen using Steve Kemp's fantastic [xen-tools]("http://xen-tools.org/software/xen-tools/") package.  I did some *cursory* research and couldn't find any Lucid templates, so I modified the existing templates.  It's not very elegant, but it appears to have gotten the job done (many VMs running for days now without problems).

UPDATE:  The dev version of xen-tools, and presumably debootstrap, has lucid/pygrub support, so pretty soon these instructions will be redundant (i.e., you might take a look at those versions as well/instead).

System:
[LIST]
[*]dom0 running Debian Lenny with kernel 2.6.26-2-xen-amd64 and Xen 3.2 (community, of course)
[*]domU Ubuntu 10.04 LTS
[/LIST]

[LIST=1]
[*]Copy files from edgy.d template (latest available) to lucid.d.
```
cp -r /usr/lib/xen-tools/edgy.d /usr/lib/xen-tools/lucid.d
```
[*]Link debootstrap gutsy profile (latest available) to lucid.
```
ln -s /usr/share/debootstrap/scripts/gutsy /usr/share/debootstrap/scripts/lucid
```
[*]Link current xen directory (many tools expect to find it here).
```
ln -s /usr/lib/xen-3.2-1 /usr/lib/xen
```
[*]Link pygrub to /usr/bin (many tools expect to find it here).
```
ln -s /usr/lib/xen/bin/pygrub /usr/bin/pygrub
```
[*]Modify /etc/xen-tools/xm.tmpl so that it lists root device first (pygrub requires this to work properly); replace the entire section following "# Disk device(s)." and preceding "# Hostname" with:
```
{
  for ( my $i = 0; $i <= $#PARTITIONS; $i++ )
  {
      if ( $PARTITIONS[$i]{'mountpoint'} eq '/' )
      {
          $OUT .= "root        = '/dev/$device" . ($i + 1) . " ro'\n";
      }
  }
  $OUT .= "disk        = [\n";
  for ( my $i = 0; $i <= $#PARTITIONS; $i++ )
  {
      if ( $PARTITIONS[$i]{'mountpoint'} eq '/' )
      {
            $OUT .= "                  '$PARTITIONS[$i]{'imagetype'}$PARTITIONS[$i]{'image'},$device" . ( $i + 1 ) .",w',\n";
      }
  }
  for ( my $i = 0; $i <= $#PARTITIONS; $i++ )
  {
      if ( $PARTITIONS[$i]{'mountpoint'} ne '/' )
      {
            $OUT .= "                  '$PARTITIONS[$i]{'imagetype'}$PARTITIONS[$i]{'image'},$device" . ( $i + 1 ) .",w',\n";
      }
  }
  $OUT .= "              ]\n";
}
```
[*]Replace the entire contents of /usr/lib/xen-tools/lucid.d/30-disable-gettys with the following (to work with non-event.d, non-inittab, hvc0 setup):
```
#!/bin/sh
#
#  This script comments out all virtual terminals which aren't on the
# first console - that must remain so that 'xm console ...' works
# correctly.
#
# Steve
# --
# http://www.steve.org.uk/
#
# Updated for Lucid; DDS/ABC
#

prefix=$1


#
#  Source our common functions
#
if [ -e /usr/lib/xen-tools/common.sh ]; then
    . /usr/lib/xen-tools/common.sh
else
    . ./hooks/common.sh
fi


#
# Log our start
#
logMessage Script $0 starting

#
#  Remove the links for upstart
#
rm ${prefix}/etc/init/tty[!1].conf


#
#  Are we using an alternative serial device?
#
if [ ! -z "${serial_device}" ]; then

    serial_device=`basename ${serial_device}`

    # Let the user know.
    logMessage "Replacing default serial device (tty1) with ${serial_device}; having destroyed the rest"

    # replace existing device.
    mv ${prefix}/etc/init/tty1.conf ${prefix}/etc/init/${serial_device}.conf
    sed -i -e s/tty1/${serial_device}/ ${prefix}/etc/init/${serial_device}.conf

    # make sure that it is allowed to login.
    echo $serial_device >> ${prefix}/etc/securetty
fi

#
#  Log our finish
#
logMessage Script $0 finished
```
[*]Create /etc/xen-tools/role.d/pygrub, and set its executable bit, with the following contents, to allow booting from the guest kernel, which is what I prefer (if you prefer to boot from dom0-supplied kernels, you can skip this); the script is based on Wejn's tremendously helpful [pygrub script]("http://wejn.org/stuff/how-to-boot-via-pygrub-on-lenny.html"), which I modified to install a newer kernel version and the linux-virtual package; note that you'll need to use this role and the pygrub role:
```
#!/bin/sh
#
#  Configure the new image to be suitable for booting via pygrub
#
# Wejn
# --
# http://wejn.org/
#
# Updated for Lucid; DDS/ABC
#


prefix=$1


#
#  Source our common functions - this will let us install a Debian package.
#
if [ -e /usr/lib/xen-tools/common.sh ]; then
    . /usr/lib/xen-tools/common.sh
else
    echo "Installation problem"
fi


#
#  Update APT lists.
#
chroot ${prefix} /usr/bin/apt-get update
 

#
#  Install the packages
#
set -e
installDebianPackage ${prefix} perl
installDebianPackage ${prefix} libklibc
installDebianPackage ${prefix} klibc-utils
installDebianPackage ${prefix} initramfs-tools
#installDebianPackage ${prefix} linux-image-2.6-xen-amd64
installDebianPackage ${prefix} linux-virtual

# Force initrd if none exists
echo ${prefix}/boot/initrd* | grep -q 2\\.6
if [ $? -ne 0 ]; then
        chroot ${prefix} update-initramfs -c -k `ls -1 ${prefix}/lib/modules/ | head -n 1`
fi

# Generate grub menu.lst
LNZ=`basename \`ls -1 ${prefix}/boot/vmlinuz*|tail -n 1\``
RD=`basename \`ls -1 ${prefix}/boot/initrd*|tail -n 1\``
mkdir -p ${prefix}/boot/grub
cat - <<-EOF > ${prefix}/boot/grub/menu.lst
default         0
timeout         5

title           Debian/Ubuntu
root            (hd0,0)
kernel          /boot/$LNZ root=/dev/xvda2 ro
initrd          /boot/$RD
EOF
```
[/LIST]
Be sure to edit your /etc/xen-tools/xen-tools.conf as appropriate (e.g., changing the distribution to lucid) and use --role=udev,pygrub when you run xen-create-image; also, comment out the kernel and initrd lines so xm defaults to pygrb; finally, you may also want to add the line "serial_console = hvc0" (no quotes) so that Xen provides the correct console based on the 30-disable-gettys script, above.  (A diff between my working xen-tools.conf and the package version is at post #3, below).  Note that this will create a VM with a root user (and password that you set if you enabled that option in xen-tools.conf).  I've written a few roles to secure the installation, including disabling the root password, which I'll try to post if I have some time.

I can produce diffs, if there's interest in the above.  Please jump in and modify the above, add to it, etc.  As I said, it's not a very elegant solution, but I needed it quickly.  (I also must apologize in advance if I'm not able to keep up with questions here, if there are any--we're a bit slammed with work at the moment.)

---

### Post by tbaptista on 2010-05-14
Great tutorial. Thanks.

I have one question.

The cfg file created for the domU had the normal kernel and initrd lines and not the pygrub bootloader line. I had to change that to enable pygrub. 

And also the console stops working midway the boot sequence. After the following lines:

> Begin: Running /scripts/init-bottom ...
Done.
mountall: Disconnected from Plymouth

Do you have any idea why? I tried to put in the cfg file the extra parameter console=hvc0, but it didn't make any difference.

Best Regards,
Tiago Baptista

---

### Post by ac4000 on 2010-05-14
Tiago, thanks for pointing that out.  In the tutorial, I missed the part where you need to comment out the kernel and initrd lines in xen-tools.conf, which causes xm to boot with pygrub (no need to call it explicitly).  I will update the above.

As for the console disconnection, I have the line
```
serial_console = hvc0
```
in xen-tools.conf, but this is supposed to be the default.  Try it and see if it changes things and, if it does, I will update the above.

Here's the diff between the package version and my xen-tools.conf:

```
--- xen-tools.conf      2008-09-29 19:08:11.000000000 -0400
+++ /etc/xen-tools/xen-tools.conf       2010-05-10 13:00:39.000000000 -0400

-# lvm = skx-vg
+lvm = xenvg

-swap   = 128Mb    # Swap size
+swap   = 512Mb    # Swap size

-dist   = etch     # Default distribution to install.
+dist   = lucid    # Default distribution to install.

-# passwd = 1
+#passwd = 1

-kernel      = /boot/vmlinuz-`uname -r`
-initrd      = /boot/initrd.img-`uname -r`
+# Undefined, to use pygrub.
+#kernel      = /boot/vmlinuz-`uname -r`
+#initrd      = /boot/initrd.img-`uname -r`

-# arch=[i386|amd64]
+arch=amd64

-# serial_device = hvc0 #default
+serial_device = hvc0 #default
+# serial_device = xvc0

-# disk_device = xvda #default
+disk_device = xvda #default
```

---

### Post by tbaptista on 2010-05-14
Yes, that solved both problems. Thanks.

Best,
Tiago

---

### Post by umuro on 2010-05-17
Followed the advice above. I get  
**Error: (2, 'Invalid kernel', 'xc_dom_find_loader: no loader found\n')**

Any ideas?

---

### Post by ac4000 on 2010-05-18
Make sure pygrub is linked properly to /usr/bin/pygrub ... that's the first thing that jumps to mind.  You could also try running pygrub directly and pointing it at the image or LV to make sure it's finding something to boot.  If that doesn't work, would you mind posting the generated config file?

---

### Post by Fanani M. Ihsan on 2010-05-20
please help me :
i was try your tutorial , but whee i running xm create show error :

fanani@server:~# xm create /etc/xen/artivisi.com.cfg 
Using config file "/etc/xen/artivisi.com.cfg".
Error: Boot loader didn't return any data!

my /etc/xen-tools/xen-tools.conf file : [here]("http://paste.ubuntu.com/436907/")
my /etc/xen/artivisi.com.cfg file : [here]("http://paste.ubuntu.com/436909/")

can u help me .
Thank for  all 

:)

---

### Post by ac4000 on 2010-05-20
Everything looks in order (my cfg doesn't have the "extra" line at the bottom, but I doubt that's causing the problem).  That said, I haven't tried this on an image, only on LVMs, so you might need to call pygrub explicitly.  You could try pointing pygrub at the image to see if you get a result (if you don't, it means it can't find the boot image for some reason).

Something like this should work:

```
pygrub /opt/serveratv/domains/artivisi.com/disk.img
```

---

### Post by wigwam_xen on 2012-01-10
@ac4000: I take your manual to install lucid as DomU. The Dom0 is based on kernel 2.6.32.18-xen0-pvops and run with xen 4.0.1. With xm list, I see the running Dom0 and everything is ok.

Now, I install lucid as a DomU exactly as you. In my xen-config for this DomU, I have the following configs:

root        = '/dev/xvda2 ro'
disk        = [
                  'file:/home/xen/domains/test/disk.img,xvda2,w',
                  'file:/home/xen/domains/test/swap.img,xvda1,w',
              ]

After that, when I create the DomU with xm create test.cfg -c, I've received this message:

init: plymouth main process (158) killed by KILL signal
init: ureadahead main process (157) killed by KILL signal
fsck from util-linux-ng 2.17.2
/dev/xvda2: clean, 18714/262144 files, 181778/1048576 blocks

Whats going wrong and how can I fix this?
Thanks for your help!

---


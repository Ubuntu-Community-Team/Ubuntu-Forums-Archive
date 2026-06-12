---
title: "ABI error building Intrepid Ibex"
date: 2008-08-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mjarmy on 2008-08-03
(I posted this question to the ubuntu-devel-discuss mailing list last night, but I think that may have been the wrong place.  I'm reposting it here instead).

I just installed 8.04 onto my Dell e1405 laptop, and now I'm trying to
build the Intrepid Ibex kernel, but I'm running into a problem.  I
cloned the git repository, updated the config files (which may not
have been necessary), and then kicked off the compile:

git clone git://kernel.ubuntu.com/ubuntu/ubuntu-intrepid.git ubuntu-intrepid
cd ubuntu-intrepid
debian/rules updateconfigs
AUTOBUILD=1 fakeroot debian/rules binary-debs

After autobuild ran for a long time, I got the following error (if I
re-run autobuild I get the error right away):

=======================================================================
II: Checking ABI for generic...
   Reading symbols/modules to ignore...read 1 symbols/modules.
   Reading new symbols (5)...read 7771 symbols.
   Reading old symbols (5)...read 7764 symbols.
II: Checking for missing symbols in new ABI...found 0 missing symbols
II: Checking for new symbols in new ABI...
   NEW : lirc_get_pdata
   NEW : lirc_register_plugin
   NEW : cmdir_write
   NEW : cmdir_read
   NEW : set_tx_channels
   NEW : lirc_unregister_plugin
   NEW : p80211_allow_ioctls
   found 7 new symbols
WW: Found new symbols within same ABI. Not recommended
II: Checking for changes to ABI...
   HASH : p80211_resume                            : 0x3e7f4a0b =>
0x91f86c1c (ignored)
   HASH : p80211wext_event_associated              : 0x5371ac73 =>
0xcbba68e3 (ignored)
   HASH : reserve_ibft_region                      : 0xd5bca5ec => 0x2d09b21a
   HASH : p80211netdev_hwremoved                   : 0x299b31d6 =>
0xf4992302 (ignored)
   HASH : wlan_setup                               : 0xd495d46e =>
0xda82d418 (ignored)
   HASH : wlan_unsetup                             : 0x31752c7a =>
0x8a56d4db (ignored)
   HASH : register_wlandev                         : 0xb9089ef4 =>
0xf1735fff (ignored)
   HASH : unregister_wlandev                       : 0x6dfdff6f =>
0x0d993080 (ignored)
   HASH : p80211_suspend                           : 0xa2bcb709 =>
0x31c95da7 (ignored)
   HASH : dump_stack                               : 0xb4e32191 => 0x6b2dc060
   HASH : p80211netdev_rx                          : 0x3dc32993 =>
0x8e1d65f3 (ignored)
   HASH : p80211skb_free                           : 0xb42124b9 =>
0x90961618 (ignored)
   HASH : p80211skb_rxmeta_attach                  : 0x83b432b7 =>
0x6672ce88 (ignored)
EE: 2 symbols changed hash and weren't ignored
II: Module hash change summary...
   ubuntu/misc/wireless/p80211/p80211      : 11
   vmlinux                                 : 2
II: Done
make: *** [abi-check-generic] Error 1
=======================================================================

There are no debs in the parent directory, so the kernel build seems
to have failed.  Can anyone help me out?

Thanks, Mike

---

### Post by BettaSharma on 2008-08-08
I built ubuntu-hardy but it did not boot. (I downloaded latest pristine sources from kernel.org and that also resulted in kernel that did not boot). The boot process halted after line "Checking 'hlt' instruction... OK" but before "SMP alternatives.. switching to UP code". I think the instructions given for kernel compilation may not be complete. Changes made to .config using menuconfig tools are wiped out by make-kpkg if the sources do not have all the right patches. There is a need for instructions to get kernel sources with proper patches.

If it is any help, I moved over to Debian (Etch) and the kernels built per instructions given in Kernel Handbook (4.2 Rebuilding an official Debian kernel package and 4.3 Building a custom kernel from Debian kernel source) worked for me.

---

### Post by InfinityCircuit on 2008-08-08
From [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

> The AUTOBUILD environment variable triggers special features in the kernel build. First, it skips normal ABI checks (ABI is the binary compatibility). It can do this because it also creates a unique ABI ID. If you used a git repo, this unique ID is generated from the git HEAD SHA. If not, it is generated from the uuidgen program (which means every time you execute the debian/rules build, the UUID will be different!). Your packages will be named using this ID.

Although it says ABI is always unique from a git pull I would be tempted to try without AUTOBUILD=1.

With that being said, I've found it easiest to just build kernels with:
make-kpkg --initrd --rootcmd fakeroot kernel_image kernel_headers

If you have a specific need for 100% compatible headers you should be able to try using the REAL debian way of fakeroot debian/rules binary.

---

### Post by BettaSharma on 2008-08-08
Infinity, You wrote:

"With that being said, I've found it easiest to just build kernels with:
make-kpkg --initrd --rootcmd fakeroot kernel_image kernel_headers
"

Is that documented anywhere?

I am especially interested in making sure I get a good source tree with all the patches and updates. The info on git has caveats on how the git repo may be inconsistent. Is there a repo where a known good source tree with all the patches etc., stays (i.e. From where I can exactly replicate a system I am running, for example). I could not find any such info (whereas in Debian, it seems very precise)

What exactly will I get when I do:

git clone git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git ubuntu-hardy

---

### Post by pdoes on 2008-10-28
I just discovered this thread but for all who are interested, I wrote up two posts on my blog about compiling a new custom kernel for Intrepid as some things have changed in the kernel compiling for Intrepid. I also ran into the ABI error but if you follow the instructions you'll be able to compile the kernel.

[How to compile a custom kernel for Ubuntu Intrepid using git]("http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid-using-git/")

[How to compile a custom kernel for Ubuntu Intrepid]("http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/")

Peter

---


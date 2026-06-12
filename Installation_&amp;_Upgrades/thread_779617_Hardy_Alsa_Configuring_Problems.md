---
title: "Hardy Alsa Configuring Problems"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by TornadoWarning40422 on 2008-05-02
Computer Specs:
Ubuntu 8.04 Gnome (after installing xubuntu 7.10 from a livecd, and installing gnome, then upgrading to hardy)
511mb Ram
Integrated Intel Ac'97 Audio Controller (revision 01)

```
downstairs@downstairs-desktop:~$ sudo m-a a-i alsa -f -i
.
Updated infos about 1 packages
Getting source for kernel version: 2.6.24-16-386
Kernel headers available in /usr/src/linux-headers-2.6.24-16-386
Creating symlink...
apt-get-y install build-essential 

Done!
download 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 7 not upgraded.
Need to get 0B/3550kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 241629 files and directories currently installed.)
Preparing to replace alsa-source 1.0.16-0ubuntu4 (using .../alsa-source_1.0.16-0ubuntu4_all.deb) ...
Unpacking replacement alsa-source ...
Setting up alsa-source (1.0.16-0ubuntu4) ...

Updating info about alsa-source

Updated infos about 1 packages
unpack 
Extracting the package tarball, /usr/src/alsa-driver.tar.bz2, please wait...
"/usr/share/modass/packages/default.sh" build KVERS=2.6.24-16-386 KSRC=/usr/src/linux KDREV=2.6.24-16.30 kdist_image
for i in control postinst postrm ; do \
		if [ -f debian/$i.orig ]; then \
			mv -f debian/$i.orig debian/$i ; \
		fi ; \
	done
rm -f control-munge
make mrproper
make[1]: Entering directory `/usr/src/modules/alsa-driver'
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'
make -C ioctl32 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make -C oss mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp mixer_oss.c pcm_oss.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make -C seq mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
make -C oss mrproper
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp seq_oss.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp seq.c seq_clientmgr.c seq_memory.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp info.c pcm.c pcm_native.c control.c hwdep.c init.c rawmidi.c sound.c timer.c memalloc.c misc.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[2]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make -C l3 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/i2c/l3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/i2c/l3'
make -C other mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp tea575x-tuner.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make -C mpu401 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp mpu401.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make -C opl3 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp opl3_lib.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make -C opl4 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make -C pcsp mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make -C vx mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp mts64.c portman2x4.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa'
make -C ad1816a mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make -C ad1848 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make -C cs423x mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make -C es1688 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make -C gus mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make -C msnd mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make -C opti9xx mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make -C sb mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp sb16_csp.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make -C wavefront mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp wavefront_fx.c wavefront_synth.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/synth'
make -C emux mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci'
make -C ac97 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ac97_codec.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make -C ali5451 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ali5451.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make -C asihpi mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make -C au88x0 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp au88x0.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make -C ca0106 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ca0106_main.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make -C cs46xx mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make -C cs5535audio mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make -C echoaudio mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp echoaudio.c darla20.c darla24.c echo3g.c gina20.c gina24.c indigo.c indigodj.c indigoio.c layla20.c layla24.c mia.c mona.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make -C emu10k1 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp emu10k1_main.c emu10k1x.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make -C hda mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp hda_codec.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make -C ice1712 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make -C korg1212 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp korg1212.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make -C mixart mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make -C nm256 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make -C oxygen mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/oxygen'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp virtuoso.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/oxygen'
make -C pcxhr mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make -C pdplus mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make -C riptide mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp riptide.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make -C rme9652 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make -C trident mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make -C vx222 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make -C ymfpci mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ymfpci_main.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ad1889.c atiixp.c atiixp_modem.c bt87x.c cmipci.c ens1370.c fm801.c intel8x0.c maestro3.c via82xx.c via82xx_modem.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[2]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make -C codecs mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make -C core mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make -C fabrics mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make -C soundbus mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make -C i2sbus mrproper
make[4]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[4]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/soc'
make -C at91 mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/soc/at91'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/soc/at91'
make -C codecs mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/soc/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/soc/codecs'
make -C fsl mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/soc/fsl'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/soc/fsl'
make -C pxa mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/soc/pxa'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/soc/pxa'
make -C s3c24xx mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make -C sh mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/soc'
make[2]: Entering directory `/usr/src/modules/alsa-driver/usb'
make -C caiaq mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/usb/caiaq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp caiaq-audio.c caiaq-device.c caiaq-input.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/usb/caiaq'
make -C usx2y mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp usX2Yhwdep.c usbusx2y.c usbusx2yaudio.c usx2yhwdeppcm.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp usbaudio.c usbmidi.c usbmixer.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make -C pdaudiocf mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make -C vx mrproper
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[2]: Entering directory `/usr/src/modules/alsa-driver/misc'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/src/modules/alsa-driver/misc'
make[2]: Entering directory `/usr/src/modules/alsa-driver/include'
rm -f .depend core *.o sndversions.h modules/*.ver modules/*.stamp
rm -f *.orig *.rej *~ .#*
rm -f linux/* asm/* media/*
make[2]: Leaving directory `/usr/src/modules/alsa-driver/include'
make[2]: Entering directory `/usr/src/modules/alsa-driver/test'
rm -f *.o mmap_test osspcm osspcm1 ossdelay
rm -f *~ *.orig *.rej .#*
make[2]: Leaving directory `/usr/src/modules/alsa-driver/test'
make[2]: Entering directory `/usr/src/modules/alsa-driver/utils'
rm -f *.orig *.rej *~ .#*
make[2]: Leaving directory `/usr/src/modules/alsa-driver/utils'
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find ../alsa-kernel -name "*~"`
find: ../alsa-kernel: No such file or directory
rm -f `find ../alsa-kernel -name "*.orig"`
find: ../alsa-kernel: No such file or directory
rm -f `find ../alsa-kernel -name "*.rej"`
find: ../alsa-kernel: No such file or directory
rm -f `find ../alsa-kernel -name ".#*"`
find: ../alsa-kernel: No such file or directory
rm -f `find ../alsa-kernel -name "out.txt"`
find: ../alsa-kernel: No such file or directory
rm -rf autom4te.cache
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
rm -f configure-stamp
rm -f build-stamp
/usr/bin/make -f debian/rules binary-modules
make[1]: Entering directory `/usr/src/modules/alsa-driver'
CC="gcc" ./configure --prefix=/usr --with-kernel=/usr/src/linux --with-build=/usr/src/linux --with-moddir=/lib/modules/2.6.24-16-386/updates/alsa --with-sequencer=yes --with-isapnp=yes --with-cards="all"
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/modules/alsa-driver
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... /usr/src/linux
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-16-386
checking for built-in ALSA... no
checking for existing ALSA module... no
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-16-386/updates/alsa
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i486
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... no
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.16
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
touch configure-stamp
/usr/bin/make  compile
make[2]: Entering directory `/usr/src/modules/alsa-driver'
/usr/bin/make dep
make[3]: Entering directory `/usr/src/modules/alsa-driver'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #2 succeeded at 156 (offset -1 lines).
Hunk #3 succeeded at 168 (offset -1 lines).
Hunk #4 succeeded at 178 (offset -1 lines).
Hunk #5 succeeded at 209 (offset -1 lines).
Hunk #6 succeeded at 494 (offset -1 lines).
Hunk #7 succeeded at 534 with fuzz 2 (offset -1 lines).
Hunk #8 succeeded at 993 (offset -1 lines).
Hunk #9 succeeded at 1022 (offset -1 lines).
copying file alsa-kernel/core/pcm.c
patching file pcm.c
Hunk #2 succeeded at 898 (offset -12 lines).
Hunk #3 succeeded at 914 (offset -12 lines).
Hunk #4 succeeded at 926 (offset -12 lines).
Hunk #5 succeeded at 980 (offset -12 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #4 succeeded at 1582 (offset -20 lines).
Hunk #5 succeeded at 2817 (offset -42 lines).
Hunk #6 succeeded at 2837 (offset -42 lines).
Hunk #7 succeeded at 2867 (offset -42 lines).
Hunk #8 succeeded at 2894 (offset -42 lines).
Hunk #9 succeeded at 2910 (offset -42 lines).
Hunk #10 succeeded at 2940 (offset -42 lines).
Hunk #11 succeeded at 3026 (offset -42 lines).
Hunk #12 succeeded at 3045 (offset -42 lines).
Hunk #13 succeeded at 3059 (offset -42 lines).
Hunk #14 succeeded at 3117 (offset -42 lines).
Hunk #15 succeeded at 3145 (offset -42 lines).
Hunk #16 succeeded at 3203 (offset -42 lines).
Hunk #17 succeeded at 3232 (offset -42 lines).
Hunk #18 succeeded at 3262 (offset -42 lines).
Hunk #19 succeeded at 3339 (offset -42 lines).
Hunk #20 succeeded at 3371 (offset -42 lines).
Hunk #21 succeeded at 3437 (offset -42 lines).
Hunk #22 succeeded at 3466 (offset -42 lines).
Hunk #23 succeeded at 3507 (offset -42 lines).
Hunk #24 succeeded at 3657 (offset -42 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #3 succeeded at 712 (offset -7 lines).
Hunk #4 succeeded at 775 (offset -11 lines).
Hunk #5 succeeded at 1383 (offset -11 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #3 succeeded at 1291 (offset 2 lines).
Hunk #4 succeeded at 1375 (offset 2 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #4 succeeded at 173 (offset -4 lines).
Hunk #5 succeeded at 247 (offset -4 lines).
Hunk #6 succeeded at 259 (offset -4 lines).
Hunk #7 succeeded at 276 (offset -4 lines).
Hunk #8 succeeded at 294 (offset -4 lines).
Hunk #9 succeeded at 343 (offset -4 lines).
Hunk #10 succeeded at 354 (offset -4 lines).
Hunk #11 succeeded at 380 (offset -4 lines).
Hunk #12 succeeded at 487 (offset -4 lines).
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #3 succeeded at 990 (offset -2 lines).
Hunk #4 succeeded at 1912 (offset -2 lines).
Hunk #5 succeeded at 1957 (offset -2 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
copying file alsa-kernel/core/misc.c
patching file misc.c
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #3 succeeded at 2589 (offset -1 lines).
Hunk #4 succeeded at 2640 (offset -1 lines).
Hunk #5 succeeded at 2763 (offset -1 lines).
Hunk #6 succeeded at 2946 (offset -1 lines).
Hunk #7 succeeded at 3073 (offset -1 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
make[6]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[6]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[4]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[5]: Entering directory `/usr/src/modules/alsa-driver/i2c/l3'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/i2c/l3'
make[5]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
copying file alsa-kernel/i2c/other/tea575x-tuner.c
patching file tea575x-tuner.c
Hunk #4 succeeded at 205 (offset 4 lines).
Hunk #5 succeeded at 228 (offset 4 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[4]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[5]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1669 (offset -2 lines).
Hunk #3 succeeded at 1714 (offset -2 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1309 (offset 2 lines).
Hunk #3 succeeded at 1352 (offset 2 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 844 (offset -2 lines).
Hunk #3 succeeded at 998 (offset -2 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3133 (offset -43 lines).
Hunk #3 succeeded at 3428 (offset -43 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2118 (offset -13 lines).
Hunk #3 succeeded at 2494 (offset -13 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #2 succeeded at 1426 (offset 23 lines).
Hunk #3 succeeded at 1607 (offset 23 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #5 succeeded at 3141 (offset 13 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #2 succeeded at 2747 (offset 2 lines).
Hunk #3 succeeded at 2933 (offset 2 lines).
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2433 (offset -3 lines).
Hunk #3 succeeded at 2443 (offset -3 lines).
Hunk #4 succeeded at 2458 (offset -3 lines).
Hunk #5 succeeded at 2469 (offset -3 lines).
Hunk #6 succeeded at 2480 (offset -3 lines).
Hunk #7 succeeded at 2563 (offset -3 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1182 (offset 2 lines).
Hunk #3 succeeded at 1242 (offset 2 lines).
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2209 (offset 4 lines).
Hunk #3 succeeded at 2379 (offset 4 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 342 (offset 1 line).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1361 (offset 8 lines).
Hunk #4 succeeded at 1730 (offset 8 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1897 (offset -29 lines).
Hunk #2 succeeded at 1960 (offset -29 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #5 succeeded at 1446 (offset 8 lines).
Hunk #6 succeeded at 1754 (offset 8 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 942 (offset 2 lines).
Hunk #3 succeeded at 1630 (offset 2 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #2 succeeded at 309 (offset 30 lines).
Hunk #3 succeeded at 347 (offset 30 lines).
Hunk #4 succeeded at 362 (offset 30 lines).
Hunk #5 succeeded at 378 (offset 30 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2353 (offset 4 lines).
Hunk #3 succeeded at 2514 (offset 4 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/oxygen'
copying file alsa-kernel/pci/oxygen/virtuoso.c
patching file virtuoso.c
Hunk #3 succeeded at 455 (offset 1 line).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/oxygen'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #3 succeeded at 2236 (offset 2 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2049 (offset 5 lines).
Hunk #3 succeeded at 2071 (offset 5 lines).
Hunk #4 succeeded at 2411 (offset 5 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[4]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[6]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[4]: Entering directory `/usr/src/modules/alsa-driver/soc'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/at91'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/at91'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/codecs'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/codecs'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/fsl'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/fsl'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/pxa'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/pxa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/sh'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/sh'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/soc'
make[4]: Entering directory `/usr/src/modules/alsa-driver/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #2 succeeded at 69 (offset -1 lines).
Hunk #3 succeeded at 685 (offset 26 lines).
Hunk #4 succeeded at 712 (offset 26 lines).
Hunk #5 succeeded at 793 (offset 26 lines).
Hunk #6 succeeded at 808 (offset 26 lines).
Hunk #7 succeeded at 1186 (offset 26 lines).
Hunk #8 succeeded at 2108 (offset 26 lines).
Hunk #9 succeeded at 2127 (offset 26 lines).
Hunk #10 succeeded at 2139 (offset 26 lines).
Hunk #11 succeeded at 2152 (offset 26 lines).
Hunk #12 succeeded at 2720 (offset 33 lines).
Hunk #13 succeeded at 2792 (offset 33 lines).
Hunk #14 succeeded at 3080 (offset 33 lines).
Hunk #15 succeeded at 3151 (offset 33 lines).
Hunk #16 succeeded at 3272 (offset 33 lines).
Hunk #17 succeeded at 3290 (offset 33 lines).
Hunk #18 succeeded at 3304 (offset 33 lines).
Hunk #19 succeeded at 3317 (offset 33 lines).
Hunk #20 succeeded at 3521 (offset 33 lines).
Hunk #21 succeeded at 3614 (offset 33 lines).
Hunk #22 succeeded at 3751 (offset 33 lines).
Hunk #23 succeeded at 3812 (offset 33 lines).
Hunk #24 succeeded at 3831 (offset 33 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 227 (offset 2 lines).
Hunk #3 succeeded at 251 (offset 2 lines).
Hunk #4 succeeded at 350 (offset 8 lines).
Hunk #5 succeeded at 1465 (offset 103 lines).
Hunk #6 succeeded at 1814 (offset 108 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb/caiaq'
copying file alsa-kernel/usb/caiaq/caiaq-audio.c
patching file caiaq-audio.c
Hunk #2 succeeded at 462 (offset 1 line).
Hunk #3 succeeded at 520 (offset 1 line).
copying file alsa-kernel/usb/caiaq/caiaq-device.c
patching file caiaq-device.c
copying file alsa-kernel/usb/caiaq/caiaq-input.c
patching file caiaq-input.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb/caiaq'
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #11 succeeded at 1057 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
Hunk #9 succeeded at 732 (offset 1 line).
Hunk #10 succeeded at 745 (offset 1 line).
Hunk #11 succeeded at 815 (offset 1 line).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[4]: Entering directory `/usr/src/modules/alsa-driver/misc'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/misc'
make[3]: Leaving directory `/usr/src/modules/alsa-driver'
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-16-386'
  CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memory_wrapper.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
  CC [M]  /usr/src/modules/alsa-driver/acore/sgbuf.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_native.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_lib.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_timer.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_misc.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_memory.o
  CC [M]  /usr/src/modules/alsa-driver/acore/rawmidi.o
  CC [M]  /usr/src/modules/alsa-driver/acore/rtctimer.o
  CC [M]  /usr/src/modules/alsa-driver/acore/timer.o
  CC [M]  /usr/src/modules/alsa-driver/acore/wrappers.o
  CC [M]  /usr/src/modules/alsa-driver/acore/misc_driver.o
  CC [M]  /usr/src/modules/alsa-driver/acore/sound.o
  CC [M]  /usr/src/modules/alsa-driver/acore/init.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memory.o
  CC [M]  /usr/src/modules/alsa-driver/acore/info.o
  CC [M]  /usr/src/modules/alsa-driver/acore/control.o
  CC [M]  /usr/src/modules/alsa-driver/acore/misc.o
  CC [M]  /usr/src/modules/alsa-driver/acore/device.o
  CC [M]  /usr/src/modules/alsa-driver/acore/isadma.o
  CC [M]  /usr/src/modules/alsa-driver/acore/sound_oss.o
  CC [M]  /usr/src/modules/alsa-driver/acore/info_oss.o
  LD [M]  /usr/src/modules/alsa-driver/acore/snd.o
  LD [M]  /usr/src/modules/alsa-driver/acore/snd-hwdep.o
  LD [M]  /usr/src/modules/alsa-driver/acore/snd-timer.o
  LD [M]  /usr/src/modules/alsa-driver/acore/snd-rtctimer.o
  LD [M]  /usr/src/modules/alsa-driver/acore/snd-pcm.o
  LD [M]  /usr/src/modules/alsa-driver/acore/snd-page-alloc.o
  LD [M]  /usr/src/modules/alsa-driver/acore/snd-rawmidi.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/mixer_oss.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/pcm_oss.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/pcm_plugin.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/io.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/copy.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/linear.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/mulaw.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/route.o
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/rate.o
  LD [M]  /usr/src/modules/alsa-driver/acore/oss/snd-mixer-oss.o
  LD [M]  /usr/src/modules/alsa-driver/acore/oss/snd-pcm-oss.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_device.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_dummy.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_midi_emul.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_midi_event.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_midi.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_virmidi.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_lock.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_clientmgr.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_memory.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_queue.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_fifo.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_prioq.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_timer.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_system.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_ports.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_info.o
  LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq.o
  LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-device.o
  LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-midi-event.o
  LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-dummy.o
  LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-virmidi.o
  LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-midi.o
  LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-midi-emul.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_init.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_timer.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_ioctl.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_event.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_rw.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_synth.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_midi.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_readq.o
  CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_writeq.o
  LD [M]  /usr/src/modules/alsa-driver/acore/seq/oss/snd-seq-oss.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/aloop.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/dummy.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/mtpav.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/mts64.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/portman2x4.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/serial-u16550.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/virmidi.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/snd-aloop.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/snd-dummy.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/snd-virmidi.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/snd-serial-u16550.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/snd-mtpav.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/snd-mts64.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/snd-portman2x4.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/mpu401/mpu401_uart.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/mpu401/mpu401.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/mpu401/snd-mpu401-uart.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/mpu401/snd-mpu401.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl3/opl3_lib.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl3/opl3_synth.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl3/opl3_seq.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl3/opl3_midi.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl3/opl3_drums.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl3/opl3_oss.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/opl3/snd-opl3-lib.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/opl3/snd-opl3-synth.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl4/opl4_lib.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl4/opl4_mixer.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl4/opl4_proc.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl4/opl4_seq.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl4/opl4_synth.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/opl4/yrw801.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/opl4/snd-opl4-lib.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/opl4/snd-opl4-synth.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/pcsp/pcsp.o
/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c: In function ‘snd_pcsp_create’:
/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c:55: error: ‘loops_per_jiffy’ undeclared (first use in this function)
/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c:55: error: (Each undeclared identifier is reported only once
/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c:55: error: for each function it appears in.)
make[6]: *** [/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.o] Error 1
make[5]: *** [/usr/src/modules/alsa-driver/drivers/pcsp] Error 2
make[4]: *** [/usr/src/modules/alsa-driver/drivers] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-16-386'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2
BUILD FAILED!
See /var/cache/modass/alsa-source.buildlog.2.6.24-16-386.1209778282 for details.

```

i have tried with and without the -f variable. nothing is working. Could someone please help?

---

### Post by TornadoWarning40422 on 2008-05-03
Well, I don't know what mysteriously went on while the computer was off, but now that I rebooted, the problem is solved. (Hmm... maybe the error was because I had already compiled this thing like four times previously) :)

---

### Post by TornadoWarning40422 on 2008-05-05
Nope, ppl. That ain't' it. For some reason I keep getting this error:

```
/home/downstairs/Desktop/alsa-driver/drivers/pcsp/pcsp.c:55: error: &#8216;loops_per_jiffy&#8217; undeclared (first use in this function)
/home/downstairs/Desktop/alsa-driver/drivers/pcsp/pcsp.c:55: error: (Each undeclared identifier is reported only once
/home/downstairs/Desktop/alsa-driver/drivers/pcsp/pcsp.c:55: error: for each function it appears in.)
make[4]: *** [/home/downstairs/Desktop/alsa-driver/drivers/pcsp/pcsp.o] Error 1
make[3]: *** [/home/downstairs/Desktop/alsa-driver/drivers/pcsp] Error 2
make[2]: *** [/home/downstairs/Desktop/alsa-driver/drivers] Error 2
make[1]: *** [_module_/home/downstairs/Desktop/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-386'
make: *** [compile] Error 2
downstairs@downstairs-desktop:~/Desktop/alsa-driver$ 

```

If it matters I don't have the linux kernel 2.6.24-16-386. I have 2.6.24-17-386. Anyway I could change what path it looks for?

---

### Post by TornadoWarning40422 on 2008-05-14
ok I got the kernel directory problem solved. something about pcsp....

```
  LD [M]  /usr/src/modules/alsa-driver/drivers/opl4/snd-opl4-lib.o
  LD [M]  /usr/src/modules/alsa-driver/drivers/opl4/snd-opl4-synth.o
  CC [M]  /usr/src/modules/alsa-driver/drivers/pcsp/pcsp.o
/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c: In function &#8216;snd_pcsp_create&#8217;:
/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c:55: error: &#8216;loops_per_jiffy&#8217; undeclared (first use in this function)
/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c:55: error: (Each undeclared identifier is reported only once
/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c:55: error: for each function it appears in.)
make[4]: *** [/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.o] Error 1
make[3]: *** [/usr/src/modules/alsa-driver/drivers/pcsp] Error 2
make[2]: *** [/usr/src/modules/alsa-driver/drivers] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-386'
make: *** [compile] Error 2
```

---

### Post by kafiland on 2008-06-12
> **TornadoWarning40422 said:**
> Nope, ppl. That ain't' it. For some reason I keep getting this error:

```
/home/downstairs/Desktop/alsa-driver/drivers/pcsp/pcsp.c:55: error: ‘loops_per_jiffy’ undeclared (first use in this function)
/home/downstairs/Desktop/alsa-driver/drivers/pcsp/pcsp.c:55: error: (Each undeclared identifier is reported only once
/home/downstairs/Desktop/alsa-driver/drivers/pcsp/pcsp.c:55: error: for each function it appears in.)
make[4]: *** [/home/downstairs/Desktop/alsa-driver/drivers/pcsp/pcsp.o] Error 1
make[3]: *** [/home/downstairs/Desktop/alsa-driver/drivers/pcsp] Error 2
make[2]: *** [/home/downstairs/Desktop/alsa-driver/drivers] Error 2
make[1]: *** [_module_/home/downstairs/Desktop/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-386'
make: *** [compile] Error 2
downstairs@downstairs-desktop:~/Desktop/alsa-driver$ 

```

If it matters I don't have the linux kernel 2.6.24-16-386. I have 2.6.24-17-386. Anyway I could change what path it looks for?


Damm, get the same problem, and no solution ...

---


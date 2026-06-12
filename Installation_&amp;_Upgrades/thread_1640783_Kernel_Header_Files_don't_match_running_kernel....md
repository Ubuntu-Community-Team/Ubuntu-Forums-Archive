---
title: "Kernel Header Files don't match running kernel..."
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by afrodeity on 2010-12-08
This is a continuation of these two threads:

[http://ubuntuforums.org/showthread.php?t=564025](http://ubuntuforums.org/showthread.php?t=564025)

[http://ubuntuforums.org/showthread.php?t=503255](http://ubuntuforums.org/showthread.php?t=503255)

in order to solve this problem

```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.37-020637rc1-generic/include

The path "/usr/src/linux-headers-2.6.37-020637rc1-generic/include" is a kernel 
header file directory, but it does not contain the file "linux/version.h" as 
expected.  This can happen if the kernel has never been built, or if you have 
invoked the "make mrproper" command in your kernel directory.  In any case, you
may want to rebuild your kernel.

```


The information here is a little outdated:
[http://hootbah.zingzam.com/2006/12/13/vmware-on-debian-etch-kernel-2-6-18-3/](http://hootbah.zingzam.com/2006/12/13/vmware-on-debian-etch-kernel-2-6-18-3/)

There is no utsrelease.h

Contents of directory

```

/usr/src/linux-headers-2.6.36-020636rc7-generic/include/linux$ ls
8250_pci.h             i2c-pnx.h            pci_regs.h
ac97_codec.h           i2c-pxa.h            pda_power.h
acct.h                 i2c-smbus.h          percpu_counter.h
acpi.h                 i2c-xiic.h           percpu-defs.h
acpi_pmtmr.h           i2o-dev.h            percpu.h
adb.h                  i2o.h                perf_event.h
adfs_fs.h              i7300_idle.h         personality.h
aer.h                  i8042.h              pfkeyv2.h
affs_hardblocks.h      i82593.h             pfn.h
agp_backend.h          i8k.h                pg.h
agpgart.h              ibmtr.h              phantom.h
ahci_platform.h        icmp.h               phonedev.h
aio_abi.h              icmpv6.h             phonet.h
aio.h                  ide.h                phy_fixed.h
altera_jtaguart.h      idr.h                phy.h
altera_uart.h          ieee80211.h          pid.h
amba                   if_addr.h            pid_namespace.h
amifd.h                if_addrlabel.h       pim.h
amifdreg.h             if_arcnet.h          pipe_fs_i.h
amigaffs.h             if_arp.h             pktcdvd.h
anon_inodes.h          if_bonding.h         pkt_cls.h
a.out.h                if_bridge.h          pkt_sched.h
apm_bios.h             if_cablemodem.h      platform_device.h
apm-emulation.h        if_ec.h              plist.h
arcdevice.h            if_eql.h             pm.h
arcfb.h                if_ether.h           pm_qos_params.h
async.h                if_fc.h              pm_runtime.h
async_tx.h             if_fddi.h            pmu.h
ata.h                  if_frad.h            pm_wakeup.h
atalk.h                if.h                 pnp.h
ata_platform.h         if_hippi.h           poison.h
ath9k_platform.h       if_infiniband.h      poll.h
atmapi.h               if_link.h            posix_acl.h
atmarp.h               if_ltalk.h           posix_acl_xattr.h
atmbr2684.h            if_macvlan.h         posix-timers.h
atmclip.h              if_packet.h          posix_types.h
atmdev.h               if_phonet.h          power
atmel-mci.h            if_plip.h            power_supply.h
atmel_pdc.h            if_ppp.h             ppdev.h
atmel-pwm-bl.h         if_pppol2tp.h        ppp_channel.h
atmel_pwm.h            if_pppox.h           ppp-comp.h
atmel_serial.h         if_slip.h            ppp_defs.h
atmel-ssc.h            if_strip.h           pps.h
atmel_tc.h             if_tr.h              pps_kernel.h
atm_eni.h              if_tun.h             prctl.h
atm.h                  if_tunnel.h          preempt.h
atm_he.h               if_vlan.h            prefetch.h
atm_idt77105.h         if_x25.h             prio_heap.h
atmioc.h               igmp.h               prio_tree.h
atmlec.h               ihex.h               proc_fs.h
atmmpc.h               ima.h                profile.h
atm_nicstar.h          in6.h                proportions.h
atmppp.h               inetdevice.h         ptp_classify.h
atmsap.h               inet_diag.h          ptrace.h
atm_suni.h             inet.h               pwm_backlight.h
atmsvc.h               inet_lro.h           pwm.h
atm_tcp.h              in.h                 pxa168_eth.h
atm_zatm.h             init.h               qnx4_fs.h
attribute_container.h  init_ohci1394_dma.h  qnxtypes.h
audit.h                initrd.h             quicklist.h
auto_dev-ioctl.h       init_task.h          quota.h
auto_fs4.h             inotify.h            quotaops.h
auto_fs.h              input                radeonfb.h
auxvec.h               input.h              radix-tree.h
ax25.h                 input-polldev.h      raid
b1lli.h                in_route.h           raid_class.h
b1pcmcia.h             intel-gtt.h          ramfs.h
backing-dev.h          intel-iommu.h        random.h
backlight.h            intel_mid_dma.h      range.h
baycom.h               intel_pmic_gpio.h    rar_register.h
bcd.h                  interrupt.h          ratelimit.h
bfs_fs.h               ioc3.h               rational.h
binfmts.h              ioc4.h               raw.h
bio.h                  iocontext.h          rbtree.h
bitmap.h               ioctl.h              rculist.h
bitops.h               io.h                 rculist_nulls.h
bitrev.h               io-mapping.h         rcupdate.h
bit_spinlock.h         iommu.h              rcutiny.h
blkdev.h               iommu-helper.h       rcutree.h
blk-iopoll.h           ioport.h             rds.h
blkpg.h                ioprio.h             reboot.h
blktrace_api.h         iova.h               reciprocal_div.h
blk_types.h            ip6_tunnel.h         regset.h
blockgroup_lock.h      ipc.h                regulator
bootmem.h              ipc_namespace.h      reiserfs_acl.h
bottom_half.h          ip.h                 reiserfs_fs.h
bpqether.h             ipmi.h               reiserfs_fs_i.h
brcmphy.h              ipmi_msgdefs.h       reiserfs_fs_sb.h
bsg.h                  ipmi_smi.h           reiserfs_xattr.h
btree-128.h            ipsec.h              relay.h
btree.h                ipv6.h               res_counter.h
btree-type.h           ipv6_route.h         resource.h
buffer_head.h          ip_vs.h              resume-trace.h
bug.h                  ipx.h                rfkill.h
byteorder              irda.h               ring_buffer.h
c2port.h               irq_cpustat.h        rio_drv.h
cache.h                irqflags.h           rio.h
caif                   irq.h                rio_ids.h
can                    irqnr.h              rio_regs.h
can.h                  irqreturn.h          rmap.h
capability.h           isa.h                romfs_fs.h
capi.h                 isapnp.h             root_dev.h
cb710.h                iscsi_boot_sysfs.h   rose.h
cciss_defs.h           iscsi_ibft.h         rotary_encoder.h
cciss_ioctl.h          isdn                 route.h
cd1400.h               isdn_divertif.h      rslib.h
cdev.h                 isdn.h               rtc
cdk.h                  isdnif.h             rtc.h
cdrom.h                isdn_ppp.h           rtc-v3020.h
cfag12864b.h           isicom.h             rtmutex.h
cgroup.h               iso_fs.h             rtnetlink.h
cgroupstats.h          istallion.h          rwlock_api_smp.h
cgroup_subsys.h        ivtvfb.h             rwlock.h
chio.h                 ivtv.h               rwlock_types.h
circ_buf.h             ixjuser.h            rwsem.h
clk.h                  jbd2.h               rwsem-spinlock.h
clockchips.h           jbd.h                rxrpc.h
clocksource.h          jffs2.h              s3c_adc_battery.h
cm4000_cs.h            jhash.h              sc26198.h
cn_proc.h              jiffies.h            scatterlist.h
cnt32_to_63.h          journal-head.h       scc.h
coda_cache.h           joystick.h           sched.h
coda_fs_i.h            jz4740-adc.h         screen_info.h
coda.h                 kallsyms.h           sctp.h
coda_linux.h           kbd_diacr.h          scx200_gpio.h
coda_psdev.h           kbd_kern.h           scx200.h
coff.h                 Kbuild               sdhci-pltfm.h
com20020.h             kbuild.h             sdla.h
compaction.h           kdb.h                seccomp.h
compat.h               kdebug.h             securebits.h
compiler-gcc3.h        kdev_t.h             security.h
compiler-gcc4.h        kd.h                 selection.h
compiler-gcc.h         kernelcapi.h         selinux.h
compiler.h             kernel.h             selinux_netlink.h
compiler-intel.h       kernel-page-flags.h  semaphore.h
completion.h           kernel_stat.h        sem.h
comstats.h             kexec.h              seq_file.h
concap.h               keyboard.h           seq_file_net.h
configfs.h             keyctl.h             seqlock.h
connector.h            key.h                serial167.h
console.h              key-type.h           serial_8250.h
consolemap.h           kfifo.h              serial_core.h
console_struct.h       kgdb.h               serial.h
const.h                klist.h              serial_max3100.h
coredump.h             kmalloc_sizes.h      serial_mfd.h
cper.h                 kmemcheck.h          serialP.h
cpufreq.h              kmemleak.h           serial_pnx8xxx.h
cpu.h                  kmod.h               serial_reg.h
cpuidle.h              kmsg_dump.h          serial_sci.h
cpumask.h              kobject.h            serio.h
cpuset.h               kobject_ns.h         sfi_acpi.h
cramfs_fs.h            kobj_map.h           sfi.h
cramfs_fs_sb.h         kprobes.h            sh_clk.h
crash_dump.h           kref.h               sh_dma.h
crc16.h                ks0108.h             sh_intc.h
crc32c.h               ks8842.h             shmem_fs.h
crc32.h                ksm.h                shm.h
crc7.h                 kthread.h            sh_pfc.h
crc-ccitt.h            ktime.h              sht15.h
crc-itu-t.h            kvm.h                sh_timer.h
crc-t10dif.h           kvm_host.h           signalfd.h
cred.h                 kvm_para.h           signal.h
crypto.h               kvm_types.h          skbuff.h
cryptohash.h           l2tp.h               slab_def.h
cs5535.h               lapb.h               slab.h
ctype.h                latencytop.h         slob_def.h
cuda.h                 lcd.h                slub_def.h
cyclades.h             lcm.h                sm501.h
cyclomx.h              leds-bd2802.h        sm501-regs.h
cycx_cfm.h             leds.h               smb_fs.h
cycx_drv.h             leds-lp3944.h        smb_fs_i.h
cycx_x25.h             leds-pca9532.h       smb_fs_sb.h
davinci_emac.h         leds_pwm.h           smb.h
dcache.h               leds-regulator.h     smb_mount.h
dca.h                  lglock.h             smbno.h
dcbnl.h                lguest.h             smc911x.h
dccp.h                 lguest_launcher.h    smc91x.h
dcookies.h             libata.h             smp.h
debugfs.h              libps2.h             smp_lock.h
debug_locks.h          license.h            smsc911x.h
debugobjects.h         limits.h             snmp.h
decompress             linkage.h            socket.h
delayacct.h            linux_logo.h         sockios.h
delay.h                lis3lv02d.h          som.h
device_cgroup.h        list.h               sonet.h
device.h               list_nulls.h         sony-laptop.h
device-mapper.h        list_sort.h          sonypi.h
devpts_fs.h            llc.h                sort.h
dio.h                  lockd                soundcard.h
dirent.h               lockdep.h            sound.h
display.h              log2.h               spi
dlmconstants.h         loop.h               spinlock_api_smp.h
dlm_device.h           lp.h                 spinlock_api_up.h
dlm.h                  lru_cache.h          spinlock.h
dlm_netlink.h          lsm_audit.h          spinlock_types.h
dlm_plock.h            lzo.h                spinlock_types_up.h
dm9000.h               m48t86.h             spinlock_up.h
dma-attrs.h            magic.h              splice.h
dma-debug.h            major.h              srcu.h
dmaengine.h            maple.h              ssb
dma-mapping.h          map_to_7segment.h    stackprotector.h
dmapool.h              marvell_phy.h        stacktrace.h
dma_remapping.h        math64.h             stallion.h
dmar.h                 matroxfb.h           start_kernel.h
dm-dirty-log.h         max17040_battery.h   statfs.h
dmi.h                  mbcache.h            stat.h
dm-ioctl.h             mbus.h               stddef.h
dm-io.h                mc146818rtc.h        stmmac.h
dm-kcopyd.h            mc6821.h             stop_machine.h
dm-log-userspace.h     mca.h                string.h
dm-region-hash.h       mca-legacy.h         string_helpers.h
dn.h                   mdio-bitbang.h       stringify.h
dnotify.h              mdio-gpio.h          sunrpc
dns_resolver.h         mdio.h               superhyway.h
dqblk_qtree.h          memblock.h           suspend.h
dqblk_v1.h             memcontrol.h         suspend_ioctls.h
dqblk_v2.h             memory.h             svga.h
dqblk_xfs.h            memory_hotplug.h     swab.h
drbd.h                 mempolicy.h          swap.h
drbd_limits.h          mempool.h            swapops.h
drbd_nl.h              memstick.h           swiotlb.h
drbd_tag_magic.h       meye.h               synclink.h
ds1286.h               mfd                  syscalls.h
ds17287rtc.h           mg_disk.h            sysctl.h
ds2782_battery.h       migrate.h            sysdev.h
dtlk.h                 mii.h                sysfs.h
dvb                    minix_fs.h           sys.h
dw_dmac.h              miscdevice.h         syslog.h
dynamic_debug.h        mISDNdsp.h           sysrq.h
early_res.h            mISDNhw.h            sysv_fs.h
edac.h                 mISDNif.h            task_io_accounting.h
edac_mce.h             mlx4                 task_io_accounting_ops.h
edd.h                  mman.h               taskstats.h
eeprom_93cx6.h         mmc                  taskstats_kern.h
efi.h                  mmdebug.h            tboot.h
efs_fs_sb.h            mm.h                 tca6416_keypad.h
efs_vh.h               mm_inline.h          tc_act
eisa.h                 mmiotrace.h          tc_ematch
elevator.h             mmtimer.h            tc.h
elfcore-compat.h       mm_types.h           tcp.h
elfcore.h              mmu_context.h        telephony.h
elf-em.h               mmu_notifier.h       termios.h
elf-fdpic.h            mmzone.h             textsearch_fsm.h
elf.h                  mnt_namespace.h      textsearch.h
elfnote.h              mod_devicetable.h    tfrc.h
enclosure.h            module.h             thermal.h
err.h                  moduleloader.h       thread_info.h
errno.h                moduleparam.h        threads.h
errqueue.h             mount.h              tick.h
etherdevice.h          mpage.h              tifm.h
ethtool.h              mqueue.h             timb_dma.h
eventfd.h              mroute6.h            timb_gpio.h
eventpoll.h            mroute.h             timecompare.h
exportfs.h             msdos_fs.h           time.h
ext2_fs.h              msg.h                timerfd.h
ext2_fs_sb.h           msi.h                timer.h
ext3_fs.h              msm_mdp.h            timeriomem-rng.h
ext3_fs_i.h            mtd                  times.h
ext3_fs_sb.h           mtio.h               timex.h
ext3_jbd.h             mutex-debug.h        tiocl.h
f75375s.h              mutex.h              tipc_config.h
fadvise.h              mv643xx_eth.h        tipc.h
falloc.h               mv643xx.h            topology.h
fanotify.h             mv643xx_i2c.h        toshiba.h
fault-inject.h         namei.h              tpm.h
fb.h                   nbd.h                trace_clock.h
fcdevice.h             ncp_fs.h             tracehook.h
fcntl.h                ncp_fs_i.h           tracepoint.h
fddidevice.h           ncp_fs_sb.h          trace_seq.h
fd.h                   ncp.h                transport_class.h
fdreg.h                ncp_mount.h          trdevice.h
fdtable.h              ncp_no.h             tsacct_kern.h
fec.h                  neighbour.h          tty_driver.h
fib_rules.h            netdevice.h          tty_flip.h
fiemap.h               net_dropmon.h        tty.h
file.h                 netfilter            tty_ldisc.h
filter.h               netfilter_arp        typecheck.h
fips.h                 netfilter_arp.h      types.h
firewire-cdev.h        netfilter_bridge     u64_stats_sync.h
firewire-constants.h   netfilter_bridge.h   uaccess.h
firewire.h             netfilter_decnet.h   ucb1400.h
firmware.h             netfilter.h          udf_fs_i.h
firmware-map.h         netfilter_ipv4       udp.h
flat.h                 netfilter_ipv4.h     uinput.h
flex_array.h           netfilter_ipv6       uio_driver.h
font.h                 netfilter_ipv6.h     uio.h
freezer.h              net.h                ultrasound.h
fscache-cache.h        netlink.h            unaligned
fscache.h              netpoll.h            un.h
fs_enet_pd.h           netrom.h             unistd.h
fs.h                   net_tstamp.h         usb
fsl_devices.h          nfs2.h               usbdevice_fs.h
fsl-diu-fb.h           nfs3.h               usb.h
fsnotify_backend.h     nfs4_acl.h           usb_usual.h
fsnotify.h             nfs4.h               user.h
fs_stack.h             nfs4_mount.h         user_namespace.h
fs_struct.h            nfsacl.h             user-return-notifier.h
fs_uart_pd.h           nfsd                 utime.h
ftrace_event.h         nfsd_idmap.h         uts.h
ftrace.h               nfs_fs.h             utsname.h
ftrace_irq.h           nfs_fs_i.h           uuid.h
fuse.h                 nfs_fs_sb.h          uwb
futex.h                nfs.h                uwb.h
gameport.h             nfs_idmap.h          vermagic.h
gcd.h                  nfs_iostat.h         version.h
genalloc.h             nfs_mount.h          veth.h
generic_acl.h          nfs_page.h           vfs.h
generic_serial.h       nfs_xdr.h            vgaarb.h
genetlink.h            nilfs2_fs.h          vga_switcheroo.h
genhd.h                nl80211.h            vhost.h
gen_stats.h            nl802154.h           via-core.h
getcpu.h               nls.h                via-gpio.h
gfp.h                  nmi.h                via.h
gfs2_ondisk.h          node.h               via_i2c.h
gigaset_dev.h          nodemask.h           videodev2.h
gpio.h                 notifier.h           videodev.h
gpio_keys.h            n_r3964.h            video_output.h
gpio_mouse.h           nsc_gpio.h           videotext.h
gsmmux.h               nsproxy.h            virtio_9p.h
hardirq.h              nubus.h              virtio_balloon.h
hash.h                 numa.h               virtio_blk.h
hdlc                   nvram.h              virtio_config.h
hdlcdrv.h              nwpserial.h          virtio_console.h
hdlc.h                 of_address.h         virtio.h
hdreg.h                of_device.h          virtio_ids.h
hid-debug.h            of_fdt.h             virtio_net.h
hiddev.h               of_gpio.h            virtio_pci.h
hid.h                  of.h                 virtio_ring.h
hidraw.h               of_i2c.h             virtio_rng.h
highmem.h              of_irq.h             vlynq.h
highuid.h              of_mdio.h            vmalloc.h
hil.h                  of_platform.h        vmstat.h
hil_mlc.h              of_spi.h             vt_buffer.h
hippidevice.h          omapfb.h             vt.h
hpet.h                 oom.h                vt_kern.h
hp_sdc.h               oprofile.h           w1-gpio.h
hrtimer.h              oxu210hp.h           wait.h
htcpld.h               padata.h             wanrouter.h
htirq.h                pageblock-flags.h    watchdog.h
hugetlb.h              page_cgroup.h        wimax
hugetlb_inline.h       page-debug-flags.h   wimax.h
hw_breakpoint.h        page-flags.h         wireless.h
hwmon.h                page-isolation.h     wlp.h
hwmon-sysfs.h          pagemap.h            wm97xx.h
hwmon-vid.h            pagevec.h            workqueue.h
hw_random.h            param.h              writeback.h
hysdn_if.h             parport.h            x25.h
i2c                    parport_pc.h         xattr.h
i2c-algo-bit.h         parser.h             xfrm.h
i2c-algo-pca.h         patchkey.h           xilinxfb.h
i2c-algo-pcf.h         path.h               yam.h
i2c-dev.h              pch_dma.h            z2_battery.h
i2c-gpio.h             pci-acpi.h           zconf.h
i2c.h                  pci-aspm.h           zlib.h
i2c-id.h               pci-dma.h            zorro.h
i2c-mux.h              pcieport_if.h        zorro_ids.h
i2c-ocores.h           pci.h                zutil.h
i2c-omap.h             pci_hotplug.h
i2c-pca-platform.h     pci_ids.h

```

any ideas?
A

---


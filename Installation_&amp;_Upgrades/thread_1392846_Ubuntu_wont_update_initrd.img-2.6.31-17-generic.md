---
title: "Ubuntu wont update initrd.img-2.6.31-17-generic"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Ziphlon on 2010-01-28
Hello when I updated my distro a little earlier today I got an error message.

Here is the whole text

```
ziphlon@ziphlon-laptop:~$ sudo dpkg --configure -a
[sudo] password for ziphlon:
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.31-17-generic
dpkg: subprocess installed post-installation script returned error exit status 1
ziphlon@ziphlon-laptop:~$ 

```Is this anything important to worry about? How do I fix it?

---

### Post by b0w on 2010-01-28
I got exactly the same problem:

Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Bus error
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.31-17-generic
dpkg: subprocess installed post-installation script returned error exit status 1
b0w@b0w-laptop:~$ 

Anyone knows how to fix this??

---

### Post by Megafag on 2010-01-28
> **b0w said:**
> I got exactly the same problem:

Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Bus error
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.31-17-generic
dpkg: subprocess installed post-installation script returned error exit status 1
b0w@b0w-laptop:~$ 

Anyone knows how to fix this??

EDIT: sorry disregard that.

---

### Post by b0w on 2010-01-29
I kept looking for help on different webs and on IRC ubuntu's help channel, somebody told me it could be my RAM so i runned memtest86 for 15 hours and everyhting is fine, not a single error on RAM, i hope someone can help with this, ill leave a verbose mode of the initramfs here:

```
b0w@b0w-laptop:~$ sudo update-initramfs -v -c -k $(uname -r)
[sudo] password for b0w: 
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/usbhid/usbhid.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-a4tech.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-apple.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-belkin.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-cherry.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-chicony.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-cypress.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-ezkey.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-gyration.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/input/ff-memless.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-logitech.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-microsoft.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-monterey.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-petalynx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-pl.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-samsung.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-sony.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-sunplus.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-tmff.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/hid/hid-zpff.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/usb-storage.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/isofs/isofs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/jfs/jfs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/net/sunrpc/sunrpc.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/net/sunrpc/auth_gss/auth_rpcgss.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/nfs_common/nfs_acl.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/lockd/lockd.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/nfs/nfs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/reiserfs/reiserfs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/lib/crc-itu-t.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/udf/udf.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/exportfs/exportfs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/xfs/xfs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/virtio/virtio.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/virtio/virtio_ring.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/virtio/virtio_pci.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/fat/fat.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/fat/vfat.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/nls/nls_cp437.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/nls/nls_iso8859-1.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/mii.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/3c59x.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/8139cp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/8139too.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/8390.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/atlx/atl1.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/atl1e/atl1e.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ssb/ssb.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/b44.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/mdio.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/cxgb3/cxgb3.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/defxx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/e100.ko
Adding binary /lib/firmware/2.6.31-17-generic/e100/d102e_ucode.bin
Adding firmware e100/d102e_ucode.bin
Adding binary /lib/firmware/2.6.31-17-generic/e100/d101s_ucode.bin
Adding firmware e100/d101s_ucode.bin
Adding binary /lib/firmware/2.6.31-17-generic/e100/d101m_ucode.bin
Adding firmware e100/d101m_ucode.bin
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/e1000/e1000.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/e1000e/e1000e.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/epic100.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/eql.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/fealnx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/forcedeth.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/hp100.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/dca/dca.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/igb/igb.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/ipg.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/myri10ge/myri10ge.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/natsemi.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/ne2k-pci.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/fs/configfs/configfs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/netconsole.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/niu.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/ns83820.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/pcnet32.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/qla3xxx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/r8169.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/s2io.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/sis900.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/skge.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/sky2.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/starfire.ko
Adding binary /lib/firmware/2.6.31-17-generic/adaptec/starfire_tx.bin
Adding firmware adaptec/starfire_tx.bin
Adding binary /lib/firmware/2.6.31-17-generic/adaptec/starfire_rx.bin
Adding firmware adaptec/starfire_rx.bin
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/sundance.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/sungem_phy.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/sungem.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/sunhme.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/tg3.ko
Adding binary /lib/firmware/2.6.31-17-generic/tigon/tg3_tso5.bin
Adding firmware tigon/tg3_tso5.bin
Adding binary /lib/firmware/2.6.31-17-generic/tigon/tg3_tso.bin
Adding firmware tigon/tg3_tso.bin
Adding binary /lib/firmware/2.6.31-17-generic/tigon/tg3.bin
Adding firmware tigon/tg3.bin
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/tlan.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/tulip/de2104x.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/tulip/de4x5.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/tulip/dmfe.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/tulip/tulip.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/tulip/winbond-840.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/tulip/xircom_cb.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/via-rhine.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/lib/crc-ccitt.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/via-velocity.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/virtio_net.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/yellowfin.ko
Copying module directory kernel/drivers/scsi
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/scsi_transport_spi.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/dmx3191d.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/st.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/fdomain.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/nsp32.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/53c700.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/sim710.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/aha152x.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/parport/parport.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/ppa.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/hptiop.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/ipr.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/scsi_tgt.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/scsi_transport_fc.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/pas16.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/gdth.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/libfc/libfc.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/fnic/fnic.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/dc395x.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/libiscsi.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/libiscsi_tcp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/cxgb3i/cxgb3i.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/atp870u.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/sym53c416.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/fd_mcs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/3w-xxxx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/stex.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/qla1280.ko
Adding binary /lib/firmware/2.6.31-17-generic/qlogic/12160.bin
Adding firmware qlogic/12160.bin
Adding binary /lib/firmware/2.6.31-17-generic/qlogic/1280.bin
Adding firmware qlogic/1280.bin
Adding binary /lib/firmware/2.6.31-17-generic/qlogic/1040.bin
Adding firmware qlogic/1040.bin
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/ultrastor.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/libsrp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/initio.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/aacraid/aacraid.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/NCR_Q720_mod.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/osst.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/eata.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/qlogicfas408.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/qlogicfas.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/NCR_D700.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/dpt_i2o.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/uio/uio.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/net/cnic.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/bnx2i/bnx2i.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/g_NCR5380.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/scsi_transport_sas.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/mpt2sas/mpt2sas.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/t128.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/tmscsim.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/wd7000.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/imm.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/device_handler/scsi_dh_alua.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/device_handler/scsi_dh_rdac.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/device_handler/scsi_dh_hp_sw.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/device_handler/scsi_dh_emc.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/megaraid.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/pcmcia/pcmcia_core.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/pcmcia/pcmcia.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/misc/enclosure.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/ses.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/in2000.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/dtc.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/u14-34f.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/fcoe/libfcoe.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/fcoe/fcoe.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/3w-9xxx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/osd/libosd.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/osd/osd.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/ips.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/raid_class.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/a100u2w.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/lpfc/lpfc.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/scsi_wait_scan.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/scsi_debug.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/scsi_transport_srp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/libsas/libsas.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/BusLogic.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/NCR53c406a.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/advansys.ko
Adding binary /lib/firmware/2.6.31-17-generic/advansys/38C1600.bin
Adding firmware advansys/38C1600.bin
Adding binary /lib/firmware/2.6.31-17-generic/advansys/38C0800.bin
Adding firmware advansys/38C0800.bin
Adding binary /lib/firmware/2.6.31-17-generic/advansys/3550.bin
Adding firmware advansys/3550.bin
Adding binary /lib/firmware/2.6.31-17-generic/advansys/mcode.bin
Adding firmware advansys/mcode.bin
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/ch.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/aha1542.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/aha1740.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/mvsas/mvsas.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/iscsi_tcp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/scsi/ibmmca.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/message/fusion/mptbase.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/message/fusion/mptscsih.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/message/fusion/mptfc.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/message/fusion/mptsas.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/message/fusion/mptspi.ko
Copying module directory kernel/drivers/block
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/DAC960.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/cpqarray.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/aoe/aoe.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/cryptoloop.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/umem.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/virtio_blk.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/floppy.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/paride.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/fit2.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/bpck.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/friq.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/pg.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/pt.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/on26.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/frpw.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/pf.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/kbic.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/comm.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/epia.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/aten.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/dstr.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/on20.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/pcd.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/ktti.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/bpck6.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/fit3.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/epat.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/paride/pd.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/nbd.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/osdblk.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/sx8.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/block/cciss.ko
Copying module directory kernel/drivers/usb/storage
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-datafab.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-sddr09.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-jumpshot.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-isd200.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-freecom.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-sddr55.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-onetouch.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-alauda.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-karma.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-cypress.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/usb/storage/ums-usbat.ko
Copying module directory kernel/drivers/ata
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_optidma.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_oldpiix.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_winbond.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/sata_via.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_it8213.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/sata_mv.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_cypress.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_cs5535.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_legacy.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_ninja32.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_hpt37x.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_radisys.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_opti.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_isapnp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ata/pata_pcmcia.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ieee1394/ieee1394.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ieee1394/ohci1394.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/ieee1394/sbp2.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/firewire/firewire-core.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/firewire/firewire-ohci.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/firewire/firewire-sbp2.ko
Adding binary /usr/share/initramfs-tools/init
Adding binary /etc/initramfs-tools/initramfs.conf
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin//busybox
Adding library /lib/libc.so.6
Adding library /lib/ld-linux.so.2
Adding binary /sbin/modprobe
Adding binary /sbin/depmod
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/libblkid.so.1
Adding library /lib/libuuid.so.1
Calling hook brltty
Adding binary /usr/share/brltty/initramfs/brltty.sh
Adding binary /sbin/brltty-setup
Calling hook compcache
Calling hook framebuffer
Copying module directory kernel/drivers/char/agp
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/agpgart.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/amd-k7-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/nvidia-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/sworks-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/sis-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/ati-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/efficeon-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/via-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/amd64-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/ali-agp.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/char/agp/intel-agp.ko
Copying module directory kernel/drivers/gpu
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/drm.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/r128/r128.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/tdfx/tdfx.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/sis/sisfb.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/sis/sis.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/i830/i830.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/i810/i810.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/ttm/ttm.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/mga/mga.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/output.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/acpi/video.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/i915/i915.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/savage/savage.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/via/via.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/console/softcursor.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/console/bitblit.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/console/font.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/console/tileblit.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/console/fbcon.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/vesafb.ko
Bus error
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/vgastate.ko
Adding module /lib/modules/2.6.31-17-generic/kernel/drivers/video/vga16fb.ko
Calling hook fuse_utils
Adding binary /sbin/mount.fuse
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library /lib/libfuse.so.2
Adding library /lib/librt.so.1
Adding library /lib/libdl.so.2
Adding library /lib/libntfs-3g.so.54
Adding library /lib/libpthread.so.0
Calling hook thermal
Calling hook udev
Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.8.so
Adding binary /sbin/udevd
Adding library /lib/libselinux.so.1
Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware.sh
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/usb_id
Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id
Adding binary /lib/udev/edd_id
Calling hook usplash
Adding binary /sbin/usplash
Adding library /lib/libusplash.so.0
Adding library /lib/libx86.so.1
Adding binary /sbin/usplash_write
Adding binary /etc/usplash.conf
Adding binary /usr/lib/usplash/usplash-artwork.so
Calling hook console_setup
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/libdevmapper.so.1.02.1
Building cpio /boot/initrd.img-2.6.31-17-generic.new initramfs
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.31-17-generic
b0w@b0w-laptop:~$ 
```

Hope anyone can help on this.
Greets!

---

### Post by b0w on 2010-02-01
Fixed it!!
well i dont know if its going to work for you but here is what i did.
First, download Hiren's Boot CD, burn the iso and everything,
Then boot from cd, on the hirens cd menu there are a lot of different apps, i went to hard drive utilities and there it has a lot of HDD recovery tools, i runned 3 different of them and they found different errors on my drive wich they fixed and thats it, the problem its gone now.
i heard it could be also your RAM so run a memtest86 from ubuntu's distro cd and check if thats the problem.
Good Luck!

---


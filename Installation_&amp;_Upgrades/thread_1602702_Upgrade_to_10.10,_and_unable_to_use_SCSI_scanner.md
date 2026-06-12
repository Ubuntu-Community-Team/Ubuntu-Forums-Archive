---
title: "Upgrade to 10.10, and unable to use SCSI scanner"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by vodsdarov on 2010-10-21
Hi,

Back in Ubuntu 10.04 my SCSI scanner (HP Scanjet 5p) was working perfectly. I just upgraded the system, and I'm totally unable to make it work.

Here's what I get from the terminal:

```
sudo sane-find-scanner
# sane-find-scanner will now attempt to detect your scanner. If the
# result is different from what you expected, first make sure your
# scanner is powered up and properly connected to your computer.

found SCSI processor "HP C5110A 3701" at /dev/sg4
# Your SCSI scanner was detected. It may or may not be supported by SANE. Try
# scanimage -L and read the backend's manpage.

found USB scanner (vendor=0x0ac8 [V Micro. Corp.], product=0x0302 [PC Camera]) at libusb:004:002
found USB scanner (vendor=0x1608 [Digi International], product=0x0240 [Edgeport/1]) at libusb:002:002
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend's manpage.

# Not checking for parallel port scanners.

# Most Scanners connected to the parallel port or other proprietary ports
# can't be detected by this program.

```


So the scanner is located. Now I grant permissions (in case that would be the problem):
```
sudo chmod o=+rw /dev/sg4
```

And I test the scanner:
```
scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

If I lauch xsane or Simple Scan utility, the result is the same... NO SCANNER IS BEING FOUND...

Any help???
Thanks in advance!

---

### Post by ttwaro on 2010-10-24
Just adding that I, too, am having a similar problem with my scsi scanner not working with xsane. I receive exactly the same messages as the previous poster with the exception that my scanner is a UMAX Astra 600S.

This scanner has worked perfectly after the last several installed releases of Ubuntu up to, and including, 10.04. After a fresh install of Ubuntu 10.10 it no longer works even though sane-find-scanner sees the device.

```
$  sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found SCSI processor "Marvell 91xx Config 1.01" at /dev/sg4
found SCSI scanner "UMAX Astra 600S V1.6" at /dev/sg5
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```
```
$  scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

---

### Post by ttwaro on 2010-10-24
Update: I ran
```
$  sudo xsane
```
and xsane came up after detecting my scanner. Of course it gave me a warning that I should NOT do this but at least I know that it is a permissions thing. I just don't know what to do at this point.

---

### Post by vhenninot on 2010-10-26
Hello,

Same problem for me...
I used chmod AND chown on the /dev/sgX device to use my AGFA scsi scanner !
But it's only working for the current session...

**Is there a possibility to grant a simple user to use the scanner ?**

I don't want to add my user to the disk group because of security issues...

any help is welcome,
Regards,
Vincent

---

### Post by vodsdarov on 2010-11-02
Thanks ttwaro.

I confirm too that using

```
sudo xsane
```

the scanner is detected and works properly.

Also changing the owner does the trick
```
sudo chown USER:GROUP /dev/sg4
sudo chmod o=+rw /dev/sg4
```

---

### Post by vodsdarov on 2010-11-02
Hi Vincent,

I'll show you the workaround I took in order to apply permanently the permissions.

First I identify the SCSI devices:
```
sudo apt-get install lsscsi
lsscsi -g
```

You might get something similar to the following:
```
    [0:0:1:0]    cd/dvd  HL-DT-ST DVDRAM GSA-4120B A102  /dev/sr0  /dev/sg0
    [2:0:2:0]    process HP       C5110A           3701  -         /dev/sg4
    [3:0:0:0]    disk    ATA      ST31000528AS     CC38  /dev/sda  /dev/sg1
    [4:0:0:0]    disk    ATA      Maxtor 6V320F0   VA11  /dev/sdb  /dev/sg2
    [5:0:0:0]    disk    ATA      MAXTOR STM332082 3.AA  /dev/sdc  /dev/sg3
```

Note that my scanner is at /dev/sg4.
Now I list the detailed info about the scanner:
```
udevadm info -a -p /sys/class/scsi_generic/sg4
```

And I get this output:
```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:14.4/0000:03:06.0/host2/target2:0:2/2:0:2:0/scsi_generic/sg4':
    KERNEL=="sg4"
    SUBSYSTEM=="scsi_generic"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:14.4/0000:03:06.0/host2/target2:0:2/2:0:2:0':
    KERNELS=="2:0:2:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="3"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="HP      "
    ATTRS{model}=="C5110A          "
    ATTRS{rev}=="3701"
    ATTRS{state}=="running"
    ATTRS{timeout}=="0"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x835"
    ATTRS{iodone_cnt}=="0x835"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{modalias}=="scsi:t-0x03"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="2"
    ATTRS{queue_type}=="none"

  looking at parent device '/devices/pci0000:00/0000:00:14.4/0000:03:06.0/host2/target2:0:2':
    KERNELS=="target2:0:2"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:14.4/0000:03:06.0/host2':
    KERNELS=="host2"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:14.4/0000:03:06.0':
    KERNELS=="0000:03:06.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="aic7xxx"
    ATTRS{vendor}=="0x9004"
    ATTRS{device}=="0x7178"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x010000"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v00009004d00007178sv00000000sd00000000bc01sc00i00"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:14.4':
    KERNELS=="0000:00:14.4"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x1002"
    ATTRS{device}=="0x4384"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060401"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v00001002d00004384sv00000000sd00000000bc06sc04i01"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

Then I create a new rule that will apply to SCSI scanners.
```
sudo gedit /etc/udev/rules.d/45-scsi-scanner.rules
```

In my case it contains the following. You might change the vendor & model according to the last command output.
```
# permissions for HP ScanJet 5p SCSI scanner
SUBSYSTEM=="scsi_generic",ATTRS{vendor}=="HP",ATTRS{model}=="C5110A", NAME="%k", SYMLINK="scanner%n", MODE="0660", GROUP="scanner"
```

Then I simply create a new system group called scanner, which will be the one with rights to use the device.
```
sudo addgroup --system scanner
```

And assign the users that are able to scan:
```
sudo adduser USERNAME scanner
```

Hope it works for you too.
All the best.

---


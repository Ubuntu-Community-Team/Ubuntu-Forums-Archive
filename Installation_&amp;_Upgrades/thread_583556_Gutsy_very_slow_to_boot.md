---
title: "Gutsy very slow to boot"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by TomGar on 2007-10-20
Hi there: Appreciate some advice.

Just upgraded my mythtv box to Gutsy. Everything works brilliantly but the boot time is terrible. It hangs in the early stages for about 3-4 minutes before going for it.

I can't work out what it is.

Machine is
mbo:asus m2npv-vm
cpu: athlon x2 4200
case: antec fusion with usb VFD and usb volume control
ram: 1gb
tv: nova-t 500 twin dvb 
remote: philips mceusb2

a cutdown dmesg from the boot is attached and the png from bootchart

Thanks.

---

### Post by Toddy on 2007-10-20
Hi TomGar.  Check out this thread: 

[http://ubuntuforums.org/showthread.php?t=581075]("http://ubuntuforums.org/showthread.php?t=581075")

The post by mahousaru resolved the problem for me.

---

### Post by TomGar on 2007-10-21
Thanks for the reply Toddy, but no dice. The usplash.conf is ok and I don't get a  blank screen just a massive pause with the usplash showing progress at about 3 bars into the boot!

Anyone getting the same?

TG

---

### Post by Alyx on 2007-10-21
Hey guys Ive been lurking for a while now and recently fresh installed 7.10. I had the same slow boot and caught this thread [http://ubuntuforums.org/showthread.php?p=3567220]("http://ubuntuforums.org/showthread.php?p=3567220")
worked like a champ!

---

### Post by TomGar on 2007-10-21
Thanks Alyx but again no dice. The big pause is coming immediately after this message hits the console
[   34.993990] usbcore: registered new interface driver dvb_usb_dib0700

which is all to do with the hauppage nova-t 500. This works perfectly when it's booted so I'm guessing the hardware driver is ok

The next console message after the freeze is

[  215.542881] lp0: using parport0 (interrupt-driven).
[  215.670384] Adding 2907724k swap on /dev/sda5.  Priority:-1 extents:1 across:2907724k

I've uploaded today's bootchart and the complete zipped dmesg.

Bootchart seems to show something going on with lirc?

Any help gratefully welcome!

TG

---

### Post by MGdesigner on 2007-10-23
Hi guys I have the  problem,too.What the same is that the kernel booting always pause after a driver loading.The driver in 7.04 works fine and also do 7.04/7.10 livecd.I have report my situation to [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/155039").

This is a serious problem.I think as many as report,Ubuntu team will handle the bug as soon.

---

### Post by Hoosier205 on 2007-10-23
Same problem here folks.

---

### Post by TomGar on 2007-10-23
I've fixed this temporarily by
apt-get remove lirc

This has given me a normal boot, however it slows right back down when I reinstall lirc.

So I'm guessing it's something in my etc/lirc/hardware.conf or in my etc/lirc/lircd.conf.

When I take these out of the way, things are normal, so I'm playing here trying to get it all working again!

Any help appreciated, below are the conf files.

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd

LIRCD_ARGS="--device=/dev/lirc0 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid --listen"
LIRCD2_ARGS="--device=/dev/lirc1 --output=/dev/lircd --pidfile=/var/run/lircd.pid --connect=localhost:8765"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""


----------------------------------------------------------------------------------------------------------------------
#
# RC-6 config file
#
# source: [http://home.hccnet.nl/m.majoor/projects__remote_control.htm](http://home.hccnet.nl/m.majoor/projects__remote_control.htm)
#         [http://home.hccnet.nl/m.majoor/pronto.pdf](http://home.hccnet.nl/m.majoor/pronto.pdf)
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Blue	0x00007ba1
	Yellow	0x00007ba2
	Green	0x00007ba3
	Red	0x00007ba4
	Teletext	0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote
begin remote
  name  ClickWheel
  bits           24
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  8
  post_data      0xFF
  gap          131993
  toggle_bit      0

  begin codes
       WheelCC                  0x010000
       WheelCW                  0x000100
       WheelClick               0x000008
  end codes
end remote

---

### Post by gazer22 on 2008-04-04
Same problem here. 

Booting hangs @ lirc.

TG and I are similar in that we're both using two IR modules.  To get that working, I had to edit the hardware.conf file as TG has, but I also modified the script in /etc/init.d/lirc to get all of the lirc settings right.  (both attached)

Example portion of messages log:
Apr  4 11:33:22 htpc kernel: [   33.844236] cx2388x v4l2 driver version 0.0.6 loaded
Apr  4 11:33:22 htpc kernel: [   33.845794] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
Apr  4 11:33:22 htpc kernel: [   33.845818] lirc_dev: lirc_register_plugin: sample_rate: 10
Apr  4 11:33:22 htpc kernel: [  213.750249] lp0: using parport0 (interrupt-driven).
Apr  4 11:33:22 htpc kernel: [  213.896043] Adding 979924k swap on /dev/sda1.  Priority:-1 extents:1 across:979924k
Apr  4 11:33:22 htpc kernel: [  214.298188] EXT3 FS on sda2, internal journal


I'm using GG with kernel: 2.6.22-14-generic
mythbuntu 7.10 install


Has anyone figured this out yet?

-jk

---

### Post by gazer22 on 2008-04-07
Okay, I got my slow boot problem fixed, and I have my Hauppauge remote and the Antec (Soundgraph) volume knob working on my Antec Fusion Black 430 case.

Here's what I did:
[LIST=1]
[*]Verify that you have the correct modules available
[LIST]
[*]For the Antec/Soundgraph Volume knob, you need lirc_imon: sudo modprobe lirc_imon
[*]For the Hauppauge remote (R808), you need lirc_i2c: sudo modprobe lirc_imon
[*]If you get errors from these modprobes, you may need to build the appropriate drivers from source (the lirc package).
[/LIST]
[*]Ensure that the devices show up as /dev/lirc0 and /dev/lirc1
[*]If the devices exist in /dev/lirc0 and /dev/lirc0, test out the remote and volume knob using "sudo mode2 -d /dev/lirc0" and "sudo mode2 -d /dev/lirc1".  You may need to kill any lircd processes that are running (check "ps -e | grep lirc" to find them).  For each device, after running mode2, hit some remote keys and/or turn the remote knob.  You should get some lines: "code: 0x00010000", or similar.
[*]Modify /etc/lirc/hardware.conf (example attached) to include:
LIRCD_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --listen"
LIRCD2_ARGS="-d /dev/lirc0 --output=/dev/lircd \
     --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"
[*]Modify hardware.conf so that it reads LOAD_MODULES=false
[*]Modify /etc/init.d/lirc (example attached) so that it matches the attached example.  The main things are to add "/usr/sbin/lircd $LIRCD2_ARGS < /dev/null"  after the start-stop-daemon line under the start case.
[*]Ensure that /etc/lirc/lircd.conf has the command maps for your hauppauge remote and the volume knob (example attached as lircd.conf.txt).
[*]Ensure that your local user's .lircrc file has maps from the remote/volume commands to mythtv (and other) commands.  Example attached as lircrc.txt.  This configuration is highly personal, so modify as needed.
[*]Ensure that /etc/modules contains the modules required (lirc_i2c and lirc_imon for me).
[*]Reboot, and cross your fingers.
[/LIST]

---


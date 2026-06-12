---
title: "Setting up fpit pen using HAL"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ace214 on 2009-07-29
I'm trying to set up my Finepoint pen to use HAL instead of xorg in my Karmic installation. (This may not be the proper forum, but I thought it would be appropriate in case there were important changes to HAL in Karmic.)

The file /usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi, which is in the default installation, triggers the following in my lshal
```
udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'
  info.callouts.add = {'hal-system-setserial'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FPI2004)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'  (string)
  input.device.set = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.id = 'FPI2004'  (string)
  pnp.serial.baud_base = 38400  (0x9600)  (int)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x3f8'  (string)
```

So, I think it is clearly picking up the pen because it picks up the correct serial port. Either that or it nows that /dev/ttyS0 refers to that serial port. But hal-system-setserial is being called with the proper line.

So, I created a file (/etc/hal/fdi/policy/fpit.fdi) to add the xorg functions to the pen, using the same match function as the previously mentioned fdi. Here's what it looks like:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
    <match key="pnp.id" contains="FPI2004">
        <append key="input.x11_driver" type="string">fpit</append>
        <append key="input.x11_options.Type" type="string">stylus</append>
        <append key="input.x11_options.InvertY" type="string">true</append>
        <append key="input.x11_options.MaximumXPositon" type="integer">12550</append>
        <append key="input.x11_options.MaximumYPositon" type="integer">7650</append>
        <append key="input.x11_options.MinimumXPositon" type="integer">400</append>
        <append key="input.x11_options.MinimumYPositon" type="integer">400</append>
        <append key="input.x11_options.SendCoreEvents" type="string">true</append>
        <append key="input.x11_options.TrackRandR" type="string">true</append>
    </match>
  </device>
</deviceinfo>

```

But it doesn't seem to be working. None of that shows up in lshal and the pen doesn't track. Any ideas?

Here's what I had in my xorg.conf for it (uncommented, of course).
```
#Section "InputDevice"
#       Identifier      "Tablet"
#       Driver          "fpit"
#       Option          "Device"                "/dev/ttyS0"
#       Option          "InvertY"
#       Option          "MaximumXPosition"      "12550"
#       Option          "MaximumYPosition"      "7650"
#       Option          "MinimumXPosition"      "400"
#       Option          "MinimumYPosition"      "400"
#       Option          "SendCoreEvents"        "True"
#       Option          "TrackRandR"
#EndSection

```

---

### Post by Favux on 2009-07-29
Hi ace214,

Maybe put a number with the .fdi like "10-fpit.fdi"?

What happens if you nest the current match line for FPI2004 inside say?:
```
    <match key="info.capabilities" contains="serial">

your stuff

    </match>

```
Sandwiched between the two device lines of course.

Also aren't you using append key where you should be using merge key?

---

### Post by ace214 on 2009-07-29
> **Favux said:**
> Hi ace214,

Maybe put a number with the .fdi like "10-fpit.fdi"?

What happens if you nest the current match line for FPI2004 inside say?:
```
    <match key="info.capabilities" contains="serial">

your stuff

    </match>

```
Sandwiched between the two device lines of course.

Also aren't you using append key where you should be using merge key?

When I tried to use merge before it gave me this in my syslog:
```
hald[2190]:error in fdi file /etc/hal/fdi/policy/30-fpit.fdi:9: Bad rule: unknown type_merge
```

Neither of your other two suggestions made a difference.

---

### Post by Favux on 2009-07-29
Hi ace214,

I'm not sure what the merge error is about.  Maybe there was a syntax error?

I was thinking of something like "10-fpit.fdi":
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

          <!-- Gateway Finepoint-Active pen devices -->
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="pnp.id" contains="FPI2004">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <merge key="input.x11_driver" type="string">fpit</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
          <merge key="input.x11_options.TrackRandR" type="string">True</merge>
          <merge key="input.x11_options.MaximumXPosition" type="string">12550</merge>
          <merge key="input.x11_options.MaximumYPosition" type="string">7650</merge>
          <merge key="input.x11_options.MinimumXPosition" type="string">400</merge>
          <merge key="input.x11_options.MinimumYPosition" type="string">400</merge>
          <merge key="input.x11_options.InvertY" type="string">True</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by ace214 on 2009-07-29
We are closer! I modified your file by taking away the serial match and it now merges the properties and I can see it on my lshal. So, I added a SendCoreEvents merge, but it doesn't track the cursor still.
My X log says this:
```
(WW) config/hal: no driver or path specified for /org/freedesktop/Hal/devices/pnp_FPI2004
```
even though the lshal shows the fpit driver
```
udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'
  info.callouts.add = {'hal-system-setserial'} (string list)
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'  (string)
  input.device.set = '/dev/ttyS0'  (string)
  input.x11_driver = 'fpit'  (string)
  input.x11_options.InvertY = 'True'  (string)
  input.x11_options.MaximumXPosition = '12550'  (string)
  input.x11_options.MaximumYPosition = '7650'  (string)
  input.x11_options.MinimumXPosition = '400'  (string)
  input.x11_options.MinimumYPosition = '400'  (string)
  input.x11_options.SendCoreEvents = 'True'  (string)
  input.x11_options.TrackRandR = 'True'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.id = 'FPI2004'  (string)
  pnp.serial.baud_base = 38400  (0x9600)  (int)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x3f8'  (string)
```

---

### Post by Favux on 2009-07-29
Hi ace214,

Good!  I thought we had to deal with the two other HAL sections:
```
udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  serial.port = 0  (0x0)  (int)
```
Especially the last one since it seems to be configuring the serial port.  Maybe the problem isn't with the serial match line but with one of these:
```
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.device" type="copy_property">serial.device</merge>
```
Did you leave them in?

Maybe we need to add the BaudRate line back in?:
```
<merge key="input.x11_options.BaudRate" type="string">38400</merge>
```

---

### Post by ace214 on 2009-07-29
> ```
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.device" type="copy_property">serial.device</merge>
```
Did you leave them in?

Maybe we need to add the BaudRate line back in?:
```
<merge key="input.x11_options.BaudRate" type="string">38400</merge>
```
Yes I left those keys in. Also, if you look towards the bottom of my lshal entry, it is still picking up the BaudRate from that 10-tabletPCs.fdi file.

Also, I tried adding the input.x11_device=/dev/ttyS0 to no avail. Still get that warning in my x log

---

### Post by Favux on 2009-07-29
Hi ace214,

Hmm...  So stepping back are we suppose to have setserial installed when configuring a serial device through HAL?  It isn't installed by default is it?  And also are we suppose to add the serial configuration line to serial.conf or not?

It seems clear we need both if we do it through xorg.conf.

---

### Post by ace214 on 2009-07-29
> **Favux said:**
> Hi ace214,

Hmm...  So stepping back are we suppose to have setserial installed when configuring a serial device through HAL?  It isn't installed by default is it?  And also are we suppose to add the serial configuration line to serial.conf or not?

It seems clear we need both if we do it through xorg.conf.

I don't know if it has to be installed, but I moved my configuration away from serial.conf to serial.conf.bak for testing the fdi, so it seems as if hal is taking care of it.

---

### Post by Favux on 2009-07-29
Hi ace214,

Since your Xlog says "no driver or path specified" I still think maybe we have to pick up the "linux.sysfs_path".

```
<match key="info.capabilities" contains="serial">
```
Works for Wacom serial tablets.  What goes wrong when you use it?  Maybe we could try to substitute:
```
<match key="info.product" contains="serial8250">
```

---

### Post by ace214 on 2009-07-29
> **Favux said:**
> Maybe we could try to substitute:
```
<match key="info.product" contains="serial8250">
```

That prevents the X options from showing up in lshal as well...

---

### Post by Favux on 2009-07-29
Hi ace214,

OK, so that picked up the first serial section too, which HAL apparently doesn't like.  So try:
```
<match key="info.subsystem" contains="tty">
```
I'm sticking to the "info's" for now.  One left.

---

### Post by Favux on 2009-07-29
Hi ace214,

The other reasonable lines seem to be:
```
<match key="info.udi" contains="serial_platform_0">

<match key="linux.device_file" contains="ttyS0">

<match key="linux.sysfs_path" contains="ttyS0">

<match key="serial.device" contains="ttyS0">
```

The way I thought we are suppose to walk (crawl?) out on the HAL device tree is to first use a match line to pick up the second serial section.  That should make the serial stuff available, including "ttyS0".  Then a second match line, FPI2004, to pick up the serial device (Finepoint Tablet) so we can load the fpit driver, and of course the BaudRate configured in 10-tabletPCs.fdi.  I don't know why it isn't working.

Edit:  Synaptic calls it "xserver-xorg-input-fpit 1:1.3.0-1 X.Org X server -- FPIT input driver".  Could we be naming it wrong?  Instead of:
```
        <merge key="input.x11_driver" type="string">fpit</merge>
```
it's suppose to be:
```
        <merge key="input.x11_driver" type="string">FPIT</merge>
```
or something?  I don't think it's case specific.

---

### Post by Favux on 2009-07-30
OK, try again.  I copied the Wacom serial tablet .fdi as closely as I could (also looking at the 10-fpit.fdi we found) along with the fpit xorg.conf entries.  I went back and looked at a serial Wacom tablet pc lshal.  Based on that and your lshal as nearly as I can tell these two match lines should pull up what we want.  Let's leave out the stylus stuff for now, because it's not in the fpit xorg.conf entries.  Hopefully the fpit driver handles that.
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

          <!-- Gateway Finepoint - Active pen devices -->
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="FPI2004">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">fpit</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
        <merge key="input.x11_options.Passive" type="string">false</merge>
          <merge key="input.x11_options.TrackRandR" type="string">true</merge>
          <merge key="input.x11_options.MaximumXPosition" type="string">12550</merge>
          <merge key="input.x11_options.MaximumYPosition" type="string">7650</merge>
          <merge key="input.x11_options.MinimumXPosition" type="string">400</merge>
          <merge key="input.x11_options.MinimumYPosition" type="string">400</merge>
          <merge key="input.x11_options.InvertY" type="string">true</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
And let's compare the lshal section(s) this generates to the one you had in post #5.

---

### Post by ace214 on 2009-07-30
That last one didn't bring up anything into the lshal...
It seems the only thing that grabs it is the pnp.id...

---

### Post by Favux on 2009-07-30
Hi ace214,

Syntax error?  Change:
```
      <match key="@info.parent:pnp.id" contains_outof="FPI2004">
```
to:
```
      <match key="@info.parent:pnp.id" contains="FPI2004">
```
Because we have only one entry in the match string.

---

### Post by ace214 on 2009-07-30
Sorry, I won't be able to test this anymore till next week- going out of town.
I'll let you know if I can get it working though.

---

### Post by Favux on 2009-08-03
Hi ace214,

We know:
```
    <match key="info.capabilities" contains="input.tablet.tabletPC">
      <match key="pnp.id" contains="FPI2004">
```
Pulls it up because in the 10-tabletPCs.fdi it sets the baud_base.  So we could try:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

          <!-- Gateway Finepoint - Active pen devices -->
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.tablet.tabletPC">
      <match key="@info.parent:pnp.id" contains="FPI2004">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">fpit</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
        <merge key="input.x11_options.Passive" type="string">false</merge>
          <merge key="input.x11_options.TrackRandR" type="string">true</merge>
          <merge key="input.x11_options.MaximumXPosition" type="string">12550</merge>
          <merge key="input.x11_options.MaximumYPosition" type="string">7650</merge>
          <merge key="input.x11_options.MinimumXPosition" type="string">400</merge>
          <merge key="input.x11_options.MinimumYPosition" type="string">400</merge>
          <merge key="input.x11_options.InvertY" type="string">true</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
and then use the second match line from 10-tabletPCs.fdi if the above second match line doesn't work.

---

### Post by ace214 on 2009-08-03
That one gives me this in lshal- no tracking and no x options...

```
udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'
  info.callouts.add = {'hal-system-setserial'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FPI2004)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'  (string)
  input.device.set = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.id = 'FPI2004'  (string)
  pnp.serial.baud_base = 38400  (0x9600)  (int)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x3f8'  (string)
```

I'm beginning to wonder if this is sort of futile since it works with xorg.conf so easily.

---

### Post by Favux on 2009-08-03
Hi ace214,

So the modification in post #16 doesn't get the .fdi in #14 to work.

The .fdi in post #18 doesn't work, even with changing the second match line.

Theoretically it shouldn't be futile.  We should be able to get a .fdi especially because we have a working xorg.conf.

Practically it appears futile.  I think I'm out of ideas.

---

### Post by ace214 on 2009-08-03
> **Favux said:**
> Hi ace214,

So the modification in post #16 doesn't get the .fdi in #14 to work.

The .fdi in post #18 doesn't work, even with changing the second match line.

Theoretically it shouldn't be futile.  We should be able to get a .fdi especially because we have a working xorg.conf.

Practically it appears futile.  I think I'm out of ideas.

Yeah, none of those modifications worked. The closest we got was getting the X message about the driver.

---

### Post by Favux on 2009-08-03
Hi ace214,

Alright, I give up.

Like I guessed a while ago maybe we're invoking the fpit driver wrong.  I'd think we would have got at least some activity with a couple of them.

Or maybe the problem is with fpit itself.  Maybe it needs to be compiled with libhal1-dev present or something.

---

### Post by Favux on 2009-08-03
So the closest we got was with:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

          <!-- Gateway Finepoint-Active pen devices -->
<deviceinfo version="0.2">
  <device>

      <match key="pnp.id" contains="FPI2004">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <merge key="input.x11_driver" type="string">fpit</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
          <merge key="input.x11_options.TrackRandR" type="string">True</merge>
          <merge key="input.x11_options.MaximumXPosition" type="string">12550</merge>
          <merge key="input.x11_options.MaximumYPosition" type="string">7650</merge>
          <merge key="input.x11_options.MinimumXPosition" type="string">400</merge>
          <merge key="input.x11_options.MinimumYPosition" type="string">400</merge>
          <merge key="input.x11_options.InvertY" type="string">True</merge>
      </match>

  </device>
</deviceinfo>
```
And if we could figure it out the key probably is:
```
(WW) config/hal: no driver or path specified for /org/freedesktop/Hal/devices/pnp_FPI2004
```
Are we missing a udev rule or something?  So fpit is recognized as a x11_driver?

---

### Post by ace214 on 2009-08-03
I don't know...

---

### Post by Favux on 2009-08-09
Hi ace214,

A stray thought occurs.

Why don't you check "/usr/lib/xorg/modules/input/" and see if the driver called something like aiptek_drv.so is present.  I think that's where the driver should be installed.  You could check the makefile for the name and the location where it is suppose to be installing.  If it isn't there you could copy it there and see if that works.

Of course if you've got it working with xorg.conf I suppose it has to be there.

---


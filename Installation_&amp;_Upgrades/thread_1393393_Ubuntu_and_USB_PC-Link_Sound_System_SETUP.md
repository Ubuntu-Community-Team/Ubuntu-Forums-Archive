---
title: "Ubuntu and USB PC-Link Sound System SETUP"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by swingboy3 on 2010-01-29
I have a radio tuner that has a USB connection to the computer.  Specifically this is a Phillips MC-500 Micro System. The cool part about this sound system is it has a USB connection for a computer.  Obviously the software was meant for windows but this also works very will for Ubuntu.  I imagine this works for most devices with "USB-PC LINK" devices made by phillips or other companies.  The usb driver is UAC3553B for this device.

I am working with a clean build of Ubuntu 9.10 Karmic

If you simply plug in this device and turn it on you can get it to almost work.  Some programs work some don't so here is how I mad it default.

Turn on the device and make sure that it is connected to your computer.

Open a terminal and:
> cd /proc/asound/
nano cards

This should display the audio cards connected to your computer.  Mine looked like this
>  0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1981B at irq 17
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf8000000
 2 [UAC3553B       ]: USB-Audio - UAC3553B
                      Philips UAC3553B at usb-0000:00:1d.0-1, full speed



Notice I have three audio cards connected in one form or another.  The first one is the onboard audio.  The second is the recorder for one of my analog video tuners.  The last one is my Phillips device.  Notice also that mine is in the DEVICE 2 slot.  This will change if you reboot with the device plugged in and turned on so make sure it is consistently either on or off when you reboot.  I choose off for mine.

Note that my machine had this driver automatically installed, it just wasn't the default device.  So now I had to make it the default device by doing this.

Open the terminal and navigate to /etc
> cd /etc
Now look to see if a file called "asound.conf" is in there.  Either way you need to either make it or edit which is simply done by:
> sudo nano asound.conf
Now just insert this code into this file someplace reasonable
> 
pcm.!default {
type hw
card 2
}

ctl.!default {
type hw
card 2
}


Replace "2" with the number that your UAC3553B device is.

That's it.  You might have to reboot, but this worked for me.

____________________________________________________________

Some things to take note of...

Some programs need to be told specifically which device is default.  Each program is different so good luck.

You need to turn on the pc-link before you start the program that will be playing the audio or it doesn't work.

If your device doesn't show up in /proc/asound/cards run dmesg grepped on UAC and see what comes up.
> dmesg |grep UAC

---

### Post by Chillkroete on 2010-12-04
Hey at all,  i tried to use my philips USB PC-Link with this tutorial and i get some sound but its realy quiet.  Can you help me ?  Greetings

---

### Post by swingboy3 on 2010-12-05
I know of three ways to adjust the volume on my system.

#1 is the volume on the Phillips device (this is pretty obvious)

#2 is by the master volume mixer that Ubuntu provides.  Itlooks like a speaker icon in the top right corner of my ubuntu screen.  This controls the master volume.  There are usually a lot of options for it.  The control for the mixer you are interested in might be turned down all the way.

#3  Is to adjust the volume on the individual program.  For example VLC has it's own volume control that you can adjust.

If you have already tried these I find it rather strange because the volume to my pc link is much louder than if I use an auxillary cable into the "line in" of the phillips box from the "line out" of my computer box.

Best of luck

---

### Post by Chillkroete on 2010-12-05
All this things are on maximum, the on strange thing is, that the philips device would not be louder if i set the volume up (on the device)

---

### Post by swingboy3 on 2010-12-05
So if I understand correctly the volume dial on your usb device does not change anything.

Are you sure that the sounds you hear are coming from your phillips device? Perhaps it is coming from an internal speaker in your computer.
Also, which device are you using (model number).

Can you control the volume with anything? (VLC or master volume control?)

Does the Phillips device ever say that it is connected?
What is your version of Ubuntu?

The other common error here is that you set the card # to the right number.  Make sure the usb connected device is disconnected upon startup of your computer or it changes the order of the /proc/asound file.

Other than that I will not be much help

---


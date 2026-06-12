---
title: "Bluetooth Keyboard not working anymore."
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by IceReaper88 on 2010-03-30
Hello,
im using the Lucid Lynx now for 2 Months without getting much problems. Yesterday my synaptic updated several packages and then i rebootet my machine...
I'm using a Logitech DiNovo Edge which is actualy an bluetooth keyboard/mouse combo with comes with its special bluetooth dongle.
Till now it worked without any problems, but since i updated yesterday it doesnt work anymore. Using any non-bluetooth keyboard works well. When i install bluetooth packages i can manualy connect to it. But that doesnt realy work either. As soon as i press a key i get a message on screen, telling me that my keyboard wants to communicate with a special app... However i am not able to connect to it at the login screen.
Whatever that update was which uses the dongle as usb dongle now did defenitly something terrible wrong. im happy i found this old keyboard, if i hadn't i couldn't even log me in!
If anyone has any suggestions or can tell me what went wrong, its would be awesome. But i think a keyboard has to work always out-of-the-box without editing configuration files.

---

### Post by Afi on 2010-03-30
Same here. It stopped working about a week a go. Some bluetooth update. It somehow enabled bluetooth, it was working as a usb devide before. I have got logitech mx900 and cordless elite keyboard thru logitech dongle. It has never worked well with bluetooth with original dongle. With almost every other bluetooth dongle mouse and keyboard works really well. Logitech must have done something funky with their dongles.

---

### Post by Caseyjp on 2010-03-30
I've submitted this bug report for this issue as my mx5000 combo is now borked as well:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288")

---

### Post by hapee on 2010-03-31
I use the Logitech DiNovo Edge also and am not able to connect it to the machine again, Bluetooth mouse is working smooth, but it is annoying to use a wired keyboard again.

---

### Post by Caseyjp on 2010-03-31
Just did daily updates plus reboot. There were updates to both bluez and gnome-bluetooth.  But nothing fixed the issue. I'm testing on a live cd and another pc to verify this issue, but right now it looks like something got borked in the settings for 'fallback' to the logitech receiver.

---

### Post by hapee on 2010-03-31
I know that if I boot the machine with Windows 7 or Karmic the keyboard works perfect so it is a Lucid issue.

---

### Post by greg606 on 2010-03-31
Hi I have the same problem under Windows7/Vmware but only after updates. So one of the updates breaks things. Which one? Any progress?

---

### Post by Caseyjp on 2010-03-31
> **hapee said:**
> I know that if I boot the machine with Windows 7 or Karmic the keyboard works perfect so it is a Lucid issue.


Arch and Karmic both function normally on the same machine.  this is definitely a regression in either bluez, or perhaps gnome-bluetooth.

---

### Post by Caseyjp on 2010-04-02
Well, still no luck.  After updating to the 2.6.32-19-generic kernel + daily updates, the mx5000 combo is STILL dead in the water.

Booting my arch install as well as karmic, the keyboard works properly, but lucid is broken as it thinks the logitech dongle is a bluetooth device rather than a usb hub.......still.

Submitted bug report 

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288")

and as of yet, noone has even looked at it, so I'm starting to wonder if this is a gnome-bluetooth issue, or something else.  Frustrating as hell to have to go grab an old usb keyboard/mouse just to test.

Also submitted [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/553964]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/553964") in the hopes that someone takes a look at this issue.

---

### Post by suchness on 2010-04-03
I think you can add those devices back using bluetooth-wizard or something commands. I have my mx5500 and mouse working fine after doing those.

---

### Post by hapee on 2010-04-04
nope the wizard does not help, in my bluetooth wizard I say the device but if I click connect the dongle and the keyboard do seem to connect (the green light stays on for a while) but it does not connect. The wizard keeps searching for any device but does not find anything in the end. It is annoying, I hope somebody will look at the reported bugs.

---

### Post by Caseyjp on 2010-04-04
Same here to no connectivity.  Not only annoying, but this should NOT be occurring.  Keyboard/mouse is critical at the beginning of the boot process, and if not there, the OS becomes useless without a fallback to other hardware which is not an acceptable solution.

The hardware does show up under hardware, but the dongle is not being seen as a USB HUB during the boot process any longer.  This is broken.

---

### Post by waspbr on 2010-04-04
That is why I always keep a spare set of USB keyboard/mouse

When you boot login as normal, then go to the the little icon or just do alt+f2  and type (if the icon is not there)

```
bluetooth-properties
```

remove your devices listed and try to search for them, it may fail once or twice but try again. 

Also you might want to try and unplug the USB adaptor and plug it back in just in case. 

my bnluetooth set is working fine, though sometimes I have to reconnect them after an upgrade.

---

### Post by Caseyjp on 2010-04-04
> **waspbr said:**
> That is why I always keep a spare set of USB keyboard/mouse

When you boot login as normal, then go to the the little icon or just do alt+f2  and type (if the icon is not there)

```
bluetooth-preferences
```

remove your devices listed and try to search for them, it may fail once or twice but try again. 

Also you might want to try and unplug the USB adaptor and plug it back in just in case. 

my bnluetooth set is working fine, though sometimes I have to reconnect them after an upgrade.

While interesting, this isn't really helpful.  Of COURSE I have a backup keyboard/mouse.  The issue is that as of a few days ago, LUCID is no longer recognizing the logitech receiver as a USB HUB.  I DON'T WANT the bluetooth stuff to have to recognize the keyboard, and currently, Karmic and Arch and other livecd distros I checked have no issue WHATSOEVER seeing the mx5000 as a USB KEYBOARD and MOUSE.

The updates to either bluez or gnome-bluetooth, have caused a regression not seen since prior to Intrepid's release that is causing this combo to fail.

Also, just an fyi, but bluetooth-preferences gives this: "command not found".

Another thing.  Starting the find device applet shows the keyboard and mouse only intermittently, and pops up this dialog:

Device 'Logitech MX1000 mouse' (00:07:61:5D:8F:A5) wants access to the service '00001124-0000-1000-8000-00805f9b34fb'.

Granting permission does NOTHING to get the process going, and shortly thereafter the mouse disappears from the add devices list.

The primary concern here is that this is a regression from Karmic which sees the receiver as a usb hub and connects with the keyboard and mouse.

Your particular system might be working fine, but you are obviously using your combo in a "bluetooth" configuration rather than the normal default...and whatever you did to get your system working is not working for the rest of us.

---

### Post by SecretofMana on 2010-04-04
I was having the same problem and after rooting around solved it by simply doing

```
sudo apt-get remove bluez*
```After this I disconnected and reconnected my mouse/keyboard and they worked fine again.

EDIT: The fix came from this bug report: [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)

EDIT2: that being said removing the entire bluez package is probably a bad idea. Can someone try removing the individual components listed in that bug report and see if it works?

EDIT3: and now my keyboard doesn't work, so I have to reinstall bluez.

---

### Post by Caseyjp on 2010-04-04
> **SecretofMana said:**
> I was having the same problem and after rooting around solved it by simply doing

```
sudo apt-get remove bluez*
```After this I disconnected and reconnected my mouse/keyboard and they worked fine again.

EDIT: The fix came from this bug report: [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)


Well...my issue seems to have cleared up as well...but not because of your solution.  

I unplugged...replugged...unplugged and then replugged the reciever several times, the last time holding in the red reset button.

The last time, for whatever reason, the utility discovered the mx5000 keyboard, requested an input of pin, and suddenly it all decided to work again. (including the mouse).

Two reboots as well as a cold shutdown later and lucid seems to remember the keyboard/mouse and works during login, only now the "bluez" applet no longer shows up in the indicator panel after things settle out...which was the way things were before this wankyness started happening in the first place.

My guess here, and its ONLY a guess after rooting through debian udev bug reports and such is that for some reason the rules don't switch the logitech bluetooth receiver from one mode to another with any reliability.  This behavior, as far as I can tell from research, started happening sometime mid-january for some users.  

Under Arch there are no issues whatsoever, and Karmic as well.  It appears that resetting the keyboard with a new passkey completely has fixed this.

My fix to this issue is more along the lines of banging on the box with a hammer, but it does seem to have done the job.:lolflag:

---

### Post by SecretofMana on 2010-04-04
And now I managed to get the keyboard and mouse both working, hopefully permanently, by following comment #5 from this bug report:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/318465](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/318465)

It's very important, especially when trying to get the receiver to detect the mouse, that you hold down the red connect button on the receiver and the mouse, as Caseyjp has noted.

---

### Post by waspbr on 2010-04-05
the command was actually 

```
bluetooth-properties
```

my bad

---

### Post by eisbaer128 on 2010-04-09
Actually had the same problem.

Unfortunatly I was not able to pair the device using bluetooth correctly. I always got "device not supporting input method". But I have the root cause for the change of behaviour. It's a bug fix inside the udev package. Looks like now it working as intended which is putting the device in bluetooth mode. If you like to avoid this behaviour just comment out in the file:

/lib/udev/rules.d/70-hid2hci.rules:

The following lines.

# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
RUN+="hid2hci --method=logitech-hid --devpath=%p"

ENV{DEVTYPE}!="usb_device", GOTO="hid2hci_end"


Result will be that the USB sticks stays in USB mode.
All of this is kind of a hack, of course

---

### Post by hapee on 2010-04-09
Well maybe the udev hack or maybe the updates were it but my Divorno is typing again, glad to got rid of the old ps2 keyboard...

---

### Post by godslam on 2010-04-12
> **eisbaer128 said:**
> Actually had the same problem.

Unfortunatly I was not able to pair the device using bluetooth correctly. I always got "device not supporting input method". But I have the root cause for the change of behaviour. It's a bug fix inside the udev package. Looks like now it working as intended which is putting the device in bluetooth mode. If you like to avoid this behaviour just comment out in the file:

/lib/udev/rules.d/70-hid2hci.rules:

The following lines.

# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
RUN+="hid2hci --method=logitech-hid --devpath=%p"

ENV{DEVTYPE}!="usb_device", GOTO="hid2hci_end"


Result will be that the USB sticks stays in USB mode.
All of this is kind of a hack, of course


Thank you so much. I did this and it seems to be working fine now. I suggest that anyone that really needs their bluetooth device(s) to work, do this.

---


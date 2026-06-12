---
title: "Mouse and keyboard stop working with 9.10 AMD 64 bit"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by CPUDave on 2010-01-11
System was running fine under 8.04 but decided to update. The live CD works fine but after install, the Mouse and Keyboard stop working under 9.10. Even the keyboard power button is off. Disconnecting and reconnecting the keyboard or the mouse does not help.

AMD Athlon 64 X2 3800+ PS/2 Keyboard and PS/2 mouse

Everything else seems OK but how would I know without the keyboard or mouse.

The keyboard turns off right before the first Ubuntu screen. The Numlock will go off and then nothing.

A re-install of 9.10 did not help.

Tried to run dpkg -  fix broken packages after booting to repair. All I get is fail to fetch http: (whatever ) ... Could not resolve us.archive.ubuntu.com.

Update: Alt-F3 ... then Booting to terminal mode does not disable the keyboard.

Any suggestions appreciated.

---

### Post by Nicolas.Perrault on 2010-01-11
Hey you know what? I had the same problem up to one month ago. I just forgot it existed due to the fact that it doesn't happen anymore. Maybe try installing updates with Synaptic?

---

### Post by garvinrick4 on 2010-01-11
Does it work in recovery boot?

---

### Post by Gen2ly on 2010-01-11
Could this be an 'acpi' issue???

---

### Post by CPUDave on 2010-01-11
Yes, it works when you select recovery and go to the shell. It appears to be a problem with the GUI because the keyboard works until the first screen where the GUI starts loading.

---

### Post by CPUDave on 2010-01-11
> **Nicolas.Perrault said:**
> Hey you know what? I had the same problem up to one month ago. I just forgot it existed due to the fact that it doesn't happen any more. Maybe try installing updates with Synaptic?

Apparently, the network is not set up yet so that will not work.

---

### Post by Nicolas.Perrault on 2010-01-12
Try connecting via ethernet cable.

---

### Post by CPUDave on 2010-01-12
> **Nicolas.Perrault said:**
> Try connecting via ethernet cable.

Already did that. It works when booted from CD, but not after install.

I also have 9.10 AMD 64 running on another 64 X2 system which had the same problem initially, but it just went away.


I am not a beginner. My first Linux install was Slackware 3.1, way back when I was looking for an alternative to OS-9. Ended up with mostly OS/2 from 94 to 05. Also used Red Hat starting with 7.1. Hmmm, my first CPU was an ET-3400 trainer and my first PC was a SWTP 6800/2.

---

### Post by CPUDave on 2010-01-17
After checking into this, I have reverted my pc back to 8.10 AMD 64 version.

There are numerous bug reports with this and similar problems that remain unresolved. This is the kind of problem that keeps WinDoze alive and limits the expansion of Linux.

It should be noted that statistically less than 1 percent of people with a problem will report it, most just go back to what ever they had before or move on to something different.

bug report    Bug #335297 is one of dozens of similar complaints that start with 9.04 and continue with 9.10 .

my page: [www.david-etheredge.name](www.david-etheredge.name)

---

### Post by 1ststallion on 2010-01-18
help!! same thing happened suddenly to my jaunty on amd64..

somebody have to solve this

---

### Post by frederickjh on 2010-02-03
Hi All!

I had the same problem with a PS2 keyboard that worked under Itrepid, Hardy and Jaunty upon upgrading to Karmic but do not have AMD processor.

This is a upstream issue. HAL now handles the automatic detection of input devices and does not always recognize them all so well.

I was able to fix this by manually configuring my keyboard. I have two different keyboard configured in my setup and some other special configs as well so I will show a very basic setup and then what I did.

First figure out what you have for a keyboard. Usually you can get into the system with a live CD and then go to the top menu: System > Preferences > Keyboard. Select the _Layouts tab_ the click the _Keyboard Model_ button. Find your model of keyboard and write it down. Then select _Generic_ under _Vendors:_ and _Evdev-managed keyboard_ under _Models:_.

You may also want to write down the keyboard layout you will be using as well. You can find the layout by clicking add and searching for it.

Hit Alt-F2 to bring up the run application dialog and type in  _gksu nautilus_ (if you are using Kbuntu you will need to use the KDE file manager instead of nautilus). Then click the run button and type in your password at the prompt. This will bring up a super user file manager. 

**[COLOR="Blue"]This means you can do bad stuff. I am not responsible if you do bad stuff. You can change files you normally cannot to protect you from yourself.[/COLOR]** 

Goto /etc/hal/fdi/policy here you will need to create a file called _x11-input.fdi_ You can do this by right clicking > Create Document > Empty File. Replace the _new file_ filename with x11-input.fdi.  Double click your new file to open it in a text editor.

You can copy and paste the code below into your new file. This will set your keyboard to be a 101 key keyboard with a US keyboard layout.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.keyboard">
      <merge key="input.x11_options.XkbModel" type="string">pc101</merge>
      <merge key="input.x11_options.XkbLayout" type="string">us</merge>
    </match>
  </device>
</deviceinfo>
```

If you need a different keyboard or keyboard layout you can look in either  /etc/X11/xkb/base.xml or /usr/share/X11/xkb/rules/base.xml (the second is a link to the first) to find the code for your keyboard.

If you open this file in gedit (the default text editor on Ubuntu)it will color code the file. You can now search for the keyboard _model_ by selecting Search > Find and typing in the model of keyboard you wrote down earlier, then click _Find_. You can do the same to find the code for layouts as well, however if the keyboard is not the default layout and a variant you will need to search for the variant name. Example US is a default keyboard US Dvorak International is a variant. In this case you would search for Dvorak International to find the code. The codes you need in either case are between the <name> and </name> tags on the line above the text you are searching for that will be between the <description> and </description> tags.

Here is how a section looks:

```
        <variant>
          <configItem>
            <name>dvorak-intl</name>
            <description>Dvorak international</description>
          </configItem>
        </variant>
        <variant>
```

Once you have found your codes change the _PC101_ to your keyboard model and _us_ to your keyboard layout.

Save x11-input.fdi and [COLOR="Red"]**reboot to see the results of your work**[/COLOR]. 

The way I understand it this file is for manually configuring devices that HAL does not recognize automatically. This can also be used to setup mice, trackballs, displays, etc. as well.

You can find more info here, however this is a freebsd website and the file paths are different that on Ubuntu.
[http://www.freebsd.org/doc/handbook/x-config.html]("http://www.freebsd.org/doc/handbook/x-config.html")

In my setup and use a dvorak international keyboard but have others that want to use the us keyboard layout, so I set this up to use the Left Alt-Shift key combination to switch between and use the useless scroll-lock keyboard light to indicate with keyboard is in use. Here is my x11-input.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.keyboard">
      <merge key="input.x11_options.XkbModel" type="string">compaqik18</merge>
      <merge key="input.x11_options.XkbLayout" type="string">us,us</merge>
      <merge key="input.x11_options.XkbVariant" type="string">intl,dvorak-intl</merge>
      <merge key="input.x11_options.XkbOptions" type="string">grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll</merge>
    </match>
  </device>
</deviceinfo>

```

I hope that this helps someone else out that is looking for this information.

Frederick

---


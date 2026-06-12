---
title: "Help! What happened to my desktop?"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by eunixd on 2007-08-24
I downloaded ubuntu through unetbootin and now my computer is starting through this MSDOS interface (or I think is the SSH server?). How do I get the gnome interface now? I can't go online, or do anything!

---

### Post by Pumalite on 2007-08-24
More details would help.

---

### Post by eunixd on 2007-08-24
I see my terminal on this black screen.

---

### Post by eunixd on 2007-08-24
I want to install the ubuntu gnome desktop.

---

### Post by Pumalite on 2007-08-24
Did you install the Server Edition? If not, try to get a command line with Crtl+Alt+F1 or F2 or Alt+F1, etc. Once there: sudo dpkg-reconfigure xserver-xorg. Accept most defaults, choose 'vesa' as your driver, then: startx

If you installed the server and all you want is a desktop; then: sudo apt-get install gnome-desktop

---

### Post by eunixd on 2007-08-24
it couldn't install x-server because no info is available. it coundn't install gnome-desktop because the package wasn't found

---

### Post by eunixd on 2007-08-24
btw I believe i installed ubuntu 7.10 (gutsy?).

---

### Post by PilotJLR on 2007-08-24
Let's see then if the internet connection works. Ping something well known, like

ping google.com


and let us know if that works. If not, then the output of "ifconfig" would be helpful.


You may want to consider downloading the 7.04 version of the Desktop OS, though. 7.10 is ALPHA software right now. If you don't know how this stuff works, then you have no reason to be messing with alpha software.

---

### Post by Pumalite on 2007-08-24
You better start fresh. Post your specs. I'd recomend Feisty 7.04 for starters. The kind of iso to download depends on your specs.

---

### Post by eunixd on 2007-08-24
the pinging didn't work. it says unknown host. I'm using a umpc so I don't have an external drive (used unetbootin).

---

### Post by eunixd on 2007-08-24
i have 786 ram and 60 gigs

---

### Post by Pumalite on 2007-08-24
What about your graphics?

---

### Post by eunixd on 2007-08-24
its an asus r2h umpc. I don't know what the graphics card is.

---

### Post by eunixd on 2007-08-24
nvm i found this:
Asus R2H Specs:

Processor: Intel Celeron-M 900 MHz
Graphics: Intel GMA 900
Operating System: Windows XP Tablet PC edition + Touch Pack
Screen: 7-inches diagonally, 800 x 480 resolution
Memory: 768 MB (1 slot accessible for user upgrade, can hold up to 1GB but sold with 512MB stick)
Hard Drive: 60GB (4200 RPM, 1.8")
Weight: 2.2 lbs
Dimensions: 9.21 in x 5.2 in x 1.3 in (width x height x depth)
Battery: 4-cell battery
Input / Output Ports:
2 regular USB 2.0 ports and one mini type USB 2.0 with a standard USB adapter included for it
VGA/Expansion out port. This can be used as a monitor out, adapter included. This can also be used as a port bar expansion dock. The dock is sold separately.
Ethernet network card port 10/100
Microphone Port
Integrated microphone
Headphone port
DC in port
AV out
GPS: SirfStarIII GPS chipset
Camera: Built-in 1.3MP video camera
Wireless: 802.11 b/g and Bluetooth integrated

---

### Post by Pumalite on 2007-08-24
I suspect your graphics, so you better go with the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) Check the box below the green sign that says: 'Start Download'

---

### Post by eunixd on 2007-08-24
i can't go online with my computer. I'm using another computer right now. Is there any way I can exit the terminal black screen?

---

### Post by Pumalite on 2007-08-24
Did you try what I said in post #5?

---

### Post by eunixd on 2007-08-24
it couldn't install x-server because no info is available

---

### Post by eunixd on 2007-08-24
can i install ubuntu through the terminal?

---

### Post by Pumalite on 2007-08-24
Yes: [http://www.wrigley.me.uk/wp/?p=71](http://www.wrigley.me.uk/wp/?p=71)

[http://ubuntuforums.org/archive/index.php/t-2068.html](http://ubuntuforums.org/archive/index.php/t-2068.html)

[http://ubuntuforums.org/archive/index.php/t-29358.html](http://ubuntuforums.org/archive/index.php/t-29358.html)

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

[http://mywheel.net/blog/index.php/ubuntu-network-install/](http://mywheel.net/blog/index.php/ubuntu-network-install/)

---

### Post by eunixd on 2007-08-24
all the links require me to download something over the internet...I only see a black terminal....xD is there something i can type on the terminal?

---

### Post by Pumalite on 2007-08-24
Better start anew. Download an Alternate CD of Feisty 7.04 and install again.

---

### Post by eunixd on 2007-08-24
Processor: Intel Celeron-M 900 MHz
Graphics: Intel GMA 900
Operating System: Windows XP Tablet PC edition + Touch Pack
Screen: 7-inches diagonally, 800 x 480 resolution
Memory: 768 MB (1 slot accessible for user upgrade, can hold up to 1GB but sold with 512MB stick)
Hard Drive: 60GB (4200 RPM, 1.8")
Weight: 2.2 lbs
Dimensions: 9.21 in x 5.2 in x 1.3 in (width x height x depth)
Battery: 4-cell battery
Input / Output Ports:
2 regular USB 2.0 ports and one mini type USB 2.0 with a standard USB adapter included for it
VGA/Expansion out port. This can be used as a monitor out, adapter included. This can also be used as a port bar expansion dock. The dock is sold separately.
Ethernet network card port 10/100
Microphone Port
Integrated microphone
Headphone port
DC in port
AV out
GPS: SirfStarIII GPS chipset
Camera: Built-in 1.3MP video camera
Wireless: 802.11 b/g and Bluetooth integrated

---

### Post by Pumalite on 2007-08-24
See my 'edited post above.

---


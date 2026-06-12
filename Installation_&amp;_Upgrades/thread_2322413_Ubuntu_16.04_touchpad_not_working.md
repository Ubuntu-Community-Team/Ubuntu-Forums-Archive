---
title: "Ubuntu 16.04 touchpad not working"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by truongkechun on 2016-04-27
I just upgraded Ubuntu from 15.10 to 16.04 and my touchpad now is not working, before it works normally, when I press button to toogle touchpad on my pc, it always display as disable (see attached file). I'm using Dell N5010. If anyone need any info, I will provide asap, please help, thanks.

---

### Post by mörgæs on 2016-04-28
How does it work in a live boot of 16.04?

---

### Post by truongkechun on 2016-04-28
I did a upgrade one, not fresh install, I upgraded from 15.10.

---

### Post by truongkechun on 2016-04-28
ah I ran this and problem solved: sudo apt-get install xserver-xorg-input-synaptics

---

### Post by vasa1 on 2016-04-28
> **truongkechun said:**
> ah I ran this and problem solved: sudo apt-get install xserver-xorg-input-synapticsI upgraded from 14.04 to 16.04 and that program is present without my having to do anything:

```
09:01 AM ~ $ apt-cache policy xserver-xorg-input-synaptics 
xserver-xorg-input-synaptics:
  Installed: 1.8.2-1ubuntu3
  Candidate: 1.8.2-1ubuntu3
  Version table:
 *** 1.8.2-1ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
09:02 AM ~ $ 
```

---

### Post by Marcial_Diaz_Toled on 2016-06-09
> **truongkechun said:**
> ah I ran this and problem solved: sudo apt-get install xserver-xorg-input-synaptics

Same scenario here, I have updated from ubuntu 14.04 to 16.04 on a Acer V5 and the touch pad stoped working, installing this package worked again, thx.

---

### Post by xyz1232 on 2016-07-03
> **truongkechun said:**
> ah I ran this and problem solved: sudo apt-get install xserver-xorg-input-synaptics

Upgraded from 15.10 to 16.04 on Dell XPS 13 9343 and found that this was required to enable the touchpad.

---

### Post by tmkasun on 2016-07-25
I'm having the same problem , My laptop is Lenovo X1 carbon , with ubuntu 16.04 just upgrade from 15.04.

---

### Post by baqarrizvi on 2016-09-05
[COLOR=#000000][I]ah I ran this and problem solved: sudo apt-get install xserver-xorg-input-synaptics
Not working suddenly stop working 

[/I]
[/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by jiapei100 on 2016-10-09
Exactly the same issue here. Touchpad does NOT work even after having xserver-xorg-input-synaptics reinstalled ...
Is it a hardware problem? -- I'm using GT72-6QE
or a software/OS problem? -- Ubuntu 16.04.1

Cheers
Pei

---

### Post by mörgæs on 2016-10-10
You could try a live boot of 16.10 (daily build of the development version) for comparison.

---

### Post by serguitus on 2016-11-03
Hi there,
I'm also having this issue with a brand new kubuntu 16.04. The touchpad of my Asus k501UW is working just as a regular mouse but no multitouch. I tried to ```apt-get install xserver-xorg-input-synaptics``` and it told me that it was already installed. accessing system settings -> input devices -> touchpad and I get a message saying "Synaptics backend *not found*"
any suggestions?
Thanks in advance

---

### Post by serguitus on 2016-11-03
Hi there,
I'm also having this issue with a brand new kubuntu 16.04.  The touchpad of my Asus k501UW is working just as a regular mouse but no  multitouch. I tried to ```apt-get install  xserver-xorg-input-synaptics``` and it told me that it was already  installed. accessing system settings -> input devices -> touchpad  and I get a message saying "Synaptics backend *not found*"
any suggestions?
Thanks in advance

---

### Post by serguitus on 2016-11-09
I think this is the actual "state of the art" with this on Asus laptops and it should be referenced for others to follow
[https://bugzilla.kernel.org/show_bug.cgi?id=120181](https://bugzilla.kernel.org/show_bug.cgi?id=120181)

---

### Post by Leon A on 2016-12-05
Here is something that fixed touchpad issues for me on some HP Stream laptops with Lubuntu 14, 15, and 16 versions.
1. create a new directory in /etc/X11/  called   xorg.conf.d
  ```
  sudo mkdir /etc/X11/xorg.conf.d
```
2. Copy the Synatptics config file from /usr/share/X11/xorg.conf.d to the new directory -file will probably start with 20- or 50 -synaptics.conf
  ```
   sudo cp 50-synaptics.conf /etc/X11/xorg.conf
```
3. Now go to the new directory and Edit the file to add two lines in the first "Input Class" section
 ```
   cd /etc/X11/xorg.conf.d
             sudo nano 50-synaptics.conf
```
 under the line saying "MatchDevicePath "/dev/input/event" in the first "InputClass" section, insert these two lines:
```
    # Enable ClickPad to fix drag/drop on some laptop models
     Option    "ClickPad"   "1"
```
4. Save and Exit editor
    Ctrl+O      Enter to confirm    Ctrl+X
5. Reboot

Now your Touchpad should support dragging and dropping

---

### Post by tiagocariolano on 2017-07-14
Hello,

I think it's possible to be a simple configuration problem. I had same problem with touchpad scroll on ubuntu 16.04 and Acer Aspire 5750 and I solved problem with "System Settings" -> "Mouse & Touchpad" and unchecked "Two finger scroll". Hope to helped.

---

### Post by bats1 on 2018-03-15
I had same problem.
This solution worked

[https://askubuntu.com/questions/763763/touchpad-under-16-04-not-working](https://askubuntu.com/questions/763763/touchpad-under-16-04-not-working)

---

### Post by vijay.govindappa90 on 2019-01-26
This worked for me on my alienware15

sudo su
echo 'blacklist i2c_hid' >> /etc/modprobe.d/blacklist.conf
depmod -a
update-initramfs -u

---

### Post by coffeecat on 2019-01-26
Back to sleep, ancient thread.

---


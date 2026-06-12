---
title: "2nd ethx driver problems 12.04"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by hawaiiman on 2012-06-10
Building a new server for my rural n.e. Thailand high school. Started with server 11.10 and messed it up. I decided to upgrade to 12.04 which cleaned up pretty well. Have an onboard ethx which runs under r8169. Our small town has a limited choice of nics. I have 2 available both tp-link: tf-3200 and tg-3468. Neither works out of the box, prefer to go with the faster pcie card the tg-3468. It requires the r8168 driver and I've got the tarball and docs on my desktop. Gedit tries to run the autorun.sh but as there is a line to remove r8169, "permission denied" as the other ethx needs it. 

lspci -nn | grep 0200 :
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168
B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)01:00.0 Ethernet controller 02.00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168
B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

according netools it sees the card and passes a few packets both ways, but a check shows no link and no IP#.
It is assigned eth0 and eth1 the onboard. The eth1 works fine and I can get on the net. I'm on my home router, so getting dhcp as the schools static IP won't go until I get there.

---

### Post by chili555 on 2012-06-10
> It requires the r8168 driver and I've got the tarball and docs on my desktop.Please try in a terminal:```
cd Desktop/8168file  [COLOR="Red"]<--or whatever you extracted from the tarball[/COLOR]
sudo install.sh
```It has been a while since I worked with that driver; the command may be:```
sudo sh install.sh
```Or even:```
sudo ./install.sh
```The sudo part takes care of the permissions problem.

Post back and let us know how it goes.

---

### Post by hawaiiman on 2012-06-10
#!/bin/sh

# invoke insmod with all arguments we got
# and use a pathname, as insmod doesn't look in . by default

TARGET_PATH=$(find /lib/modules/$(uname -r)/kernel/drivers/net -name realtek -type d)
if [ "$TARGET_PATH" = "" ]; then
    TARGET_PATH=/lib/modules/$(uname -r)/kernel/drivers/net
fi
echo
echo "Check old driver and unload it." 
check=`lsmod | grep r8169`
if [ "$check" != "" ]; then
        echo "rmmod r8169"
        /sbin/rmmod r8169
fi

check=`lsmod | grep r8168`
if [ "$check" != "" ]; then
        echo "rmmod r8168"
        /sbin/rmmod r8168
fi

echo "Build the module and install"
echo "-------------------------------" >> log.txt
date 1>>log.txt
make $@ all 1>>log.txt || exit 1
module=`ls src/*.ko`
module=${module#src/}
module=${module%.ko}

if [ "$module" = "" ]; then
    echo "No driver exists!!!"
    exit 1
elif [ "$module" != "r8169" ]; then
    if test -e $TARGET_PATH/r8169.ko ; then
        echo "Backup r8169.ko"
        if test -e $TARGET_PATH/r8169.bak ; then
            i=0
            while test -e $TARGET_PATH/r8169.bak$i
            do
                i=$(($i+1))
            done
            echo "rename r8169.ko to r8169.bak$i"
            mv $TARGET_PATH/r8169.ko $TARGET_PATH/r8169.bak$i
        else
            echo "rename r8169.ko to r8169.bak"
            mv $TARGET_PATH/r8169.ko $TARGET_PATH/r8169.bak
        fi
    fi
fi

echo "DEPMOD $(uname -r)"
depmod `uname -r`
echo "load module $module"
modprobe $module

is_update_initramfs=n
distrib_list="ubuntu debian"

if [ -r /etc/debian_version ]; then
    is_update_initramfs=y
elif [ -r /etc/lsb-release ]; then
    for distrib in $distrib_list
    do
        /bin/grep -i "$distrib" /etc/lsb-release 2>&1 /dev/null && \
            is_update_initramfs=y && break
    done
fi

if [ "$is_update_initramfs" = "y" ]; then
    if which update-initramfs >/dev/null ; then
        echo "Updating initramfs. Please wait."
        update-initramfs -u -k $(uname -r)
    else
        echo "update-initramfs: command not found"
        exit 1
    fi
fi

echo "Completed."
exit 0
I am guessing that as the onboard eth uses the r8169 driver, it shouldn't be removed

---

### Post by chili555 on 2012-06-10
Did you run the command in a terminal as I suggested? This simply looks like a display of the install.sh file.

I think you _do_ want to replace r8169 with r8168.

---

### Post by hawaiiman on 2012-06-10
Yes I ran the autorun.sh as su
if the r8169 is off, fine and good for the nic, but (and I have tried rmmod r8169, which kills the onboard eth1

---

### Post by hawaiiman on 2012-06-10
I gave you some inaccurate information. When i run autorun.sh it does start to run the script, but stops with "remove r8169 not permitted" the terminal closes as soon as I try to click on it to copy and paste here.

---

### Post by hawaiiman on 2012-06-11
I had an "aha" moment. I reasoned that the "lessor of two weevils" would be to get an identical tg-3468 ethx card. Then in one session rm the r8169 and then the autorun.sh should run to completion. Both cards will run on the same driver and the onboard ethx will become a victim of progress......?

---

### Post by hawaiiman on 2012-06-11
Ok, so both tg-3468 cards are in. Ran rmmod r8169. I have discovered that the onboard runs realtek 8111b and confirmed r8169 driver, but this driver only gives partial functionality to an 8111c card. I read elsewhere that the 8111b chipset will run under r8168. We will see. In either case, I'm covered. I ran the autorun.sh again and it got past the rm8169 objection only to hang again on the next command. It responded that it would not move the mentioned lib file. I'll wait for response from you.

---

### Post by chili555 on 2012-06-11
Please try it again this way in a terminal:```
cd Desktop/8168file  [COLOR="Red"]<--or whatever you extracted from the tarball[/COLOR]
sudo su
./install.sh
exit
```The object of the script is to compile a new, hopefully better driver r8168 and remove r8169 and put r8168 in its place. The new r8168 will drive all of these devices:> spci -nn | grep 0200 :
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168
B PCI Express Gigabit Ethernet controller [[COLOR="Red"]10ec:8168[/COLOR]] (rev 01)01:00.0 Ethernet controller 02.00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168
B PCI Express Gigabit Ethernet controller [[COLOR="Red"]10ec:8168[/COLOR]] (rev 03)In order to do so, the script must run successfully to completion.

---

### Post by hawaiiman on 2012-06-11
/Desktop/r8168/r8168-8.031.00$
./install.sh
bash: /install.sh no such file or directory

same result with: /install.sh   ,    /autorun.sh
./autorun.sh   starts auturun.sh  yes

Check old driver and unload it.
Build the module and install
cp: cannot create regular file  /lib/modules/3.2.0-24-generic-pae/kernel/drivers
Backup r8169.ko
rename r8169.ko to r8169.bak
mv: cannot move    /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/ethernet/ret/realtek/r8169.bak': Permission denied     [I had previously ran rmmod r8169...?]
DEPMOD 3.2.0-24-generic-pae
FATAL: Could not open /lib/modules/3.2.0-24-generic-pae/modules.dep.temp for writing: Permission denied
DEPMOD 3.2.0-24-generic-pae
FATAL: Could not open /lib/modules/3.2.0-24-generic-pae/modules.dep.temp for writing: Permission denied
load module r8168
FATAL: Module not found.
Updating initramsfs. Please wait.
lm: failed to create hard link  /boot/initrd.tmg.img-3.2.0-24-generic-pae.dpkg-bak'
=>  /boot/initrd.img-3.2.0-24-generic-pae': Operation not permitted
cp cannot create regular file  /boot/initd.img-3.2.0-24-generic-pae.dpkg-bak': Permission denied
Completed.

wish I could copy and paste,but windows won't read linux files, so type out..hope I got it all right. I have no idea where this puts me at this point.....

---

### Post by chili555 on 2012-06-11
> /Desktop/r8168/r8168-8.031.00[COLOR="Red"]$[/COLOR]
./install.sh
bash: /install.sh no such file or directory

same result with: /install.sh , /autorun.sh
./autorun.sh starts auturun.sh yes
That little symbol I highlighted indicates you are running as an ordinary user, not a super user. Please recall:```
cd Desktop/8168file  <--or whatever you extracted from the tarball
[COLOR="Red"]sudo su[/COLOR]
./autorun.sh
exit
```Please try again. I'll be around for a few hours.

---

### Post by hawaiiman on 2012-06-11
Uhh I can't find the tilde on this keyboard. The lines I copied are preceded by the tilde. I entered gksudo su at the beginning. I am running with th full desktop, so I believe gksudo is the appropriate command (?). Sorry I'm such a noob.
I can be here as long as it takes, and thanks again for your help.

---

### Post by chili555 on 2012-06-11
I can't see where or how you need the tilde. Help me. Please close the terminal. Open a new one and type exactly this and no more:```
cd Desktop/r8168-8.031.00/  [COLOR="Red"]<--or whatever you extracted from the tarball[/COLOR]
sudo su
./autorun.sh
exit
```

EDIT: Attached is the only reason I think it works.

---

### Post by hawaiiman on 2012-06-11
Duh!! I've gotten shell shocked apparently. OK!! All three eth ports are up! The onboard is now eth1and connected with WAN access, and I'm on the server now. The other two flash 2 lights out of four when either is connected to the laptop. Laptop connects but "no network access" and "unknown network" server reports " wired network disconnected". Great progress, however.

---

### Post by chili555 on 2012-06-11
So what do we need to work on next? Pick one pressing problem and we'll knock it down.

---

### Post by hawaiiman on 2012-06-11
The pcie based nicks still aren't linking or getting IP#, so they aren't as yet usable for LAN.

---

### Post by chili555 on 2012-06-11
> **hawaiiman said:**
> The pcie based nicks still aren't linking or getting IP#, so they aren't as yet usable for LAN.So you have four NICs in this server? What are they to attach to? How does the server get its internet? A DSL modem or cable modem?

Are you using Network Manager or have you configured /etc/network/interfaces?

We are getting out of my areas of expertise. I am quick to admit that I don't know everything about everything.

---

### Post by hawaiiman on 2012-06-11
I have 2 pcie cards . I will probably take one out after I get at least 2 working. One is WAN (the onboard) and is fine now. The other 2 are pretty much where they were when I started. I'm going to try a reboot. That may get them up. The only thing I've used is the network tools.

---

### Post by chili555 on 2012-06-11
> The only thing I've used is the network tools.By this, I assume you mean Network Manager. It isn't designed for a server and isn't going to manage 3-4 NICs. 

Again, what are they to attach to? How does the server get its internet? A DSL modem or cable modem?

EDIT: Off for the evening. I have a headache and her name is Realtek.

---

### Post by hawaiiman on 2012-06-11
I shut down and pulled the extra card. So now only the 2 ethernet devices, one the onboard 8111b device which is fine and up, and the other the pcie card which is 8111c. I have the pcie card plugged in to my laptop. The server is set for dhcp and getting internet from my home ADSL thru a wireless router, modem, switch via cat5 cable. So it's getting a 192.168.1.3 from NAT. Although the wire from the pcie is in the laptop and they see each other, the laptop is getting internet from the wifi side of the router currently.
Actually your headache name is Hawaiiman, but I appreciate the courtesy.

---

### Post by chili555 on 2012-06-12
I am assuming that the objective is for the server to share the internet it now has with the laptop. I suggest you study this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)  There are also numerous forum posts here about ICS: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

We are now officially outside my area of expertise. I'm not sure I have much left to contribute.

---

### Post by hawaiiman on 2012-06-12
No,the laptop is just a test. The school now has over 20 clients running wxp, a website (down due to dying hp ml350), a multi-media room, and this week we're adding 12 more clients, each with digi projectors. Oh, we host email too.
You've been extremely helpful and PATIENT!! (caps deserved here) Thanks so much!

---

### Post by hawaiiman on 2012-06-16
I took some time off to get some perspective. I decided that the best approach was to re-install. So I did a fresh install of 12.04 server 64bit. I was using the wong version, I discovered. TP-Link kindly sent me a newer version of the driver. All went fine, driver went in with autorun.sh perfectly. I have the onboard as eth0 and it'son the net with ip 192.168.1.4 . 
So what I'm wondering is, whether my idea that I could accomplish anything valid by attempting to make it run on my home system with a simple LAN was even a valid approach. It seems like a lot of work to do and to take it to school and change everything. I have a key to the server cave at school. I would prefer to work at home. I recall in phsics that the application of force alone is not considered work.....
I brought home the crimper and some rj-45's so I'll make a crossover cable. I connected through the routr with it's adsl cable disconnected aand the ping stopped at the 192.168.1.1 (router). One question: How does eth1 know it's supporting a LAN and not the WAN and vice versa for the eth0 ? Assuming I'm at school at the isp interface (fiber to eth converter), I would assign the available second staic IP we own to this machine. I would then assign the gateway we use. This would be like the entries in the readme file of the driver info I sent. to go in : /etc/network/interfaces  via gedit...?
I'd then use the same source to set eth1 for auto and dhcp...? Does it need a gateway reference?
I wish there was a simple step by step guide for setting up a server under Ubuntu server 12.04. The install is well covered.

---

### Post by chili555 on 2012-06-16
> One question: How does eth1 know it's supporting a LAN and not the WAN and vice versa for the eth0 ? Assuming I'm at school at the isp interface (fiber to eth converter), I would assign the available second staic IP we own to this machine. I would then assign the gateway we use. This would be like the entries in the readme file of the driver info I sent. to go in : /etc/network/interfaces via gedit...?
I'd then use the same source to set eth1 for auto and dhcp...? Does it need a gateway reference?We are now well outside the area of my expertise, but the sort answer is yes, these declarations belong in /etc/network/interfaces. Network Manager, if it's installed, will likely not do what you need. I'd remove it.

Typically a server doesn't run a GUI windowing manager which Network Manager requires.

This may help: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I'm sorry I can't be of more assistance. They only let me fiddle with easy stuff here.

---

### Post by hawaiiman on 2012-09-28
Well, the nic problem never got resolved. I just couldn't find a way of getting an IP assigned to it. So it was parked. In the mean time the school changed isp's and now has PPPoe. We now plan to use an enterprise router for firewall and filtering, etc. We would like to have the Ubuntu server as a DNS cache. That means I've got the thing at home again (I'm on PPPoe also). Formatted the drives and went to 32 bit server 12.04. Ran update and upgrade. /lib/modules shows both 3.2.0-23-generic-pae and 3.2.0-31-generic-pae. 
Downloaded r8168-8.032.00 from realtek and ran autorun.sh as root. Process halts with:
 
make[2]: ***no rule to make target 'clean'. Stop
make[1]: *** [clean] Error 2
make: *** [clean} Error 2
 
As both -23 and -31 are shown in /lib/modules, could this be the problem?

---

### Post by chili555 on 2012-09-28
> make[2]: ***no rule to make target 'clean'. Stop
make[1]: *** [clean] Error 2
make: *** [clean} Error 2I suspect you haven't installed linux-headers-generic and build-essential. They are...essential!

Then try the install script again.

---

### Post by hawaiiman on 2012-09-28
OK, I had the header package, but not build-essential. I just got that and re-booted, tried ./autorun.sh and got exactly the same error message as last time.

---

### Post by chili555 on 2012-09-29
You *do* have linux-headers for your running kernel?```
sudo dpkg -s linux-headers-`uname -r` | head -n3
sudo dpkg -s build-essential | head -n3

```Those tickmarks are on the same key with ~.

Did you?```
cd r8168-8.032.00
sudo su
./autorun.sh
exit
```It works perfectly for me.

---

### Post by hawaiiman on 2012-09-29
Yes I had done apt-get install linux-headers 3.2.0-23-generic-pae and same for ...-31..  the former installed ok and the later said it was latest already. Unfortunately, the same error message appears when I run ./autorun.sh
 
Interestingly I tried:
"
# Internal LAN interfaceauto eth1iface eth1 inet static   address 10.10.0.1   netmask 255.255.255.0Then on the laptop go into Network and in the properties of your wired connection set:
IP 10.10.0.100
Subnet 255.255.255.0
Gateway 10.10.0.1
DNS 8.8.8.8 (Google DNS for example)

Then open command prompt on the laptop and try:
ping 10.10.0.1

That should return the ping from your server. If all of that works out, you're good to go.

At that moment the laptop will still not have full internet access.

On the server open /etc/sysctl.conf to edit with:
sudo nano /etc/sysctl.conf

Uncomment (remove the # from the start of) the line saying net.ipv4.ip_forward=1

Save the changes with Ctrl + O and exit nano with Ctrl + X."

This got the laptop and server to ping each other and IP shows in net tools of server.
 
Then:
 
"Then on the server do:
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

Now test if your laptop has internet access through the server. It should."
Unfortuneately this part didn't work . I am using the IP of the adsl router as the DNS, as that's what comes back on this tower, which is connected to the same router.

---

### Post by hawaiiman on 2012-09-29
BTW when I installed 12.04 I initially selected no additional packages. I have since installed dnsmasq and commented out dnsmasq from network manager, as a step towards using dnsmasq as a DNS cache

---

### Post by hawaiiman on 2012-09-29
Hey, good news! r8168 is in, I went back to 64 bit. I used the above suggestion for setting eth2 (in this case, the LAN nic) to 10.10.0.1, etc. and it worked! The laptop gets on the internet nicely through switch, then server. Something in the" iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE " string makes the change temporary and goes away after re-boot. Would you know how to make the change to the iptables permanent?

---

### Post by chili555 on 2012-09-29
> **hawaiiman said:**
> Hey, good news! r8168 is in, I went back to 64 bit. I used the above suggestion for setting eth2 (in this case, the LAN nic) to 10.10.0.1, etc. and it worked! The laptop gets on the internet nicely through switch, then server. Something in the" iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE " string makes the change temporary and goes away after re-boot. Would you know how to make the change to the iptables permanent?No, sorry. I'm not an iptables man. I'm sure it can be done. You might start a new thread with iptables in the title to catch the attention of the gurus.

---

### Post by hawaiiman on 2012-09-29
Ok, thank you very much for ypur help. How do I mark this solved?

---

### Post by chili555 on 2012-09-29
> **hawaiiman said:**
> Ok, thank you very much for ypur help. How do I mark this solved?Use Thread Tools at the top.

---

### Post by hawaiiman on 2012-10-11
So the server was working, but no firewall or dns cache. I set up ufw as recommended and when I turned it on my internet connection was blocked. After trying several recommended "solutions" nothing worked. I kept reading about conflicting packages in 12.04, network manager issues, etc. I've got a 3 week holiday, so I formatted and decided to install 10.04 server LTS with (as yet) no GUI. Unfortunately I'm back to the ./autorun.sh won't finish problem. I get the same error "make: *** No rule to make target `all' . Stop."
I've run apt-get dist-upgrade apt-get linux-headers-2.6.32-44-generic apt-get install build-essential apt-get update apt-get upgrade .
Just as before the kernel has r8169 but not r8168 so ifconfig doesn't show eth1
Obviously eth0 has working internet access. The failed ./autorun.sh removes r8169 but that's easily fixed with modprobe r8169
I've got the r8168 package in my flash drive, and can get that mounted ok. so I do have access to the driver package.

---

### Post by chili555 on 2012-10-12
> I get the same error "make: *** No rule to make target `all' . Stop."Please be sure you have build-essential and linux-headers installed.

---

### Post by hawaiiman on 2012-10-12
> **hawaiiman said:**
> ... "make: *** No rule to make target `all' . Stop."
I've run apt-get dist-upgrade apt-get linux-headers-2.6.32-44-generic,` apt-get install build-essential' apt-get update, apt-get upgrade ...
 
Those were at the top of my list after I upgraded to the 2.6.32-44
as I read the lines go by there was a lot of mention of headers, but I went ahead and installed as I've shown here. I realize I've missed something.
"linux-headers-2.6.32-44-server is already the newest version."
"build-essential is already the newest version"

---

### Post by chili555 on 2012-10-12
Please give me a link to the file you downloaded to compile. I'd like to examine it.

---

### Post by hawaiiman on 2012-10-12
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

---

### Post by chili555 on 2012-10-12
It autoruns perfectly for me. Did you try:```
cd Desktop/r8168-8.032.00/  [COLOR="Red"]<--or wherever you extracted it[/COLOR]
sudo su
./autorun.sh
exit
```If it still won't build as sudo su, please attach the log.txt to your reply using the paperclip tool at the top of the reply box.

---

### Post by hawaiiman on 2012-10-20
works perfect! my mistake, I tried to drop autorun.sh into a folder alone and run from there. Lesson learned. Thanks very much!

---

### Post by chili555 on 2012-10-20
Glad it's working. Have fun!

---


---
title: "Installing Programs"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by Bone Crusher on 2009-11-14
If I have downloaded on my desktop a program, and I open the terminal, which command will install it?

---

### Post by bernardfrancois on 2009-11-14
That depends on the program.

Normally, you should first check if the program is available in synaptic and install it there (hit Ctrl+F2 and enter 'gksudo synaptic' to launch synaptic).

If it's not available there, can you provide some more info about the file you opened? Does it have a certain file extension (e.g. .deb or .tar.gz or .tgz)? You may first have to extract it and then show us what's inside. If it had to be extracted first, you can look for a file named 'readme' and read it's contents.

If you still can't solve this, you could also post a list of the files inside.

---

### Post by Bone Crusher on 2009-11-15
This is the read me. I really need to get the wireless working and have no idea what to do.



<Linux device driver for Realtek Ethernet controllers>

    This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D Gigabit Ethernet controllers with PCI-Express interface.

<Requirements>

    - Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
    - For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
    - Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
    Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
        # lsmod | grep r8169

    If it is installed, please remove it.
        # rmmod r8169
    note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

    Unpack the tarball :
        # tar vjxf r8168-8.aaa.bb.tar.bz2

    Change to the directory:
        # cd r8168-8.aaa.bb

    If you are running the target kernel, then you should be able to do :

        # make clean modules    (as root or with sudo)
        # make install
        # depmod -a
        # modprobe r8168

    You can check whether the driver is loaded by using following commands.

        # lsmod | grep r8168
        # ifconfig -a

    If there is a device name, ethX, shown on the monitor, the linux 
    driver is loaded. Then, you can use the following command to activate 
    the ethX.

        # ifconfig ethX up

        ,where X=0,1,2,...

<Set the network related information>
    1. Set manually
        a. Set the IP address of your machine.

            # ifconfig ethX "the IP address of your machine" 

        b. Set the IP address of DNS.

           Insert the following configuration in /etc/resolv.conf.
        
            nameserver "the IP address of DNS"

        c. Set the IP address of gateway.

            # route add default gw "the IP address of gateway"

    2. Set by doing configurations in /etc/sysconfig/network-scripts
       /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
       /ifcfg-ethX for SuSE. There are two examples to set network 
       configurations.

        a. Fix IP address:
            DEVICE=eth0
            BOOTPROTO=static
            ONBOOT=yes
            TYPE=ethernet
            NETMASK=255.255.255.0
            IPADDR=192.168.1.1
            GATEWAY=192.168.1.254
            BROADCAST=192.168.1.255

        b. DHCP:
            DEVICE=eth0
            BOOTPROTO=dhcp
            ONBOOT=yes    

<Modify the MAC address>
    There are two ways to modify the MAC address of the NIC.
    1. Use ifconfig:

        # ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

       ,where X is the device number assigned by Linux kernel, and
          YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

    2. Use ip:

        # ip link set ethX address YY:YY:YY:YY:YY:YY

       ,where X is the device number assigned by Linux kernel, and
          YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

    1. Force the link status when insert the driver.

       If the user is in the path ~/r8168, the link status can be forced 
       to one of the 5 modes as following command.

        # insmod ./src/r8168.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

        ,where
            SPEED_MODE    = 1000    for 1000Mbps
                    = 100    for 100Mbps
                    = 10    for 10Mbps
            DUPLEX_MODE    = 0    for half-duplex
                    = 1    for full-duplex
            NWAY_OPTION    = 0    for auto-negotiation off (true force)
                    = 1    for auto-negotiation on (nway force)
        For example:

            # insmod ./src/r8168.ko speed=100 duplex=0 autoneg=1

        will force PHY to operate in 100Mpbs Half-duplex(nway force).

    2. Force the link status by using ethtool.
        a. Insert the driver first.
        b. Make sure that ethtool exists in /sbin.
        c. Force the link status as the following command.

            # ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

            ,where
                SPEED_MODE    = 1000    for 1000Mbps
                        = 100    for 100Mbps
                        = 10    for 10Mbps
                DUPLEX_MODE    = half    for half-duplex
                        = full    for full-duplex
                NWAY_OPTION    = off    for auto-negotiation off (true force)
                        = on    for auto-negotiation on (nway force)

        For example:
        
            # ethtool -s eth0 speed 100 duplex full autoneg on

        will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
    Transmitting Jumbo Frames, whose packet size is bigger than 1500 bytes, please change mtu by the following command.

    # ifconfig ethX mtu MTU

    , where X=0,1,2,..., and MTU is configured by user.

    RTL8168B/8111B supports Jumbo Frame size up to 4 kBytes.
    RTL8168C/8111C and RTL8168CP/8111CP support Jumbo Frame size up to 6 kBytes.
    RTL8168D/8111D supports Jumbo Frame size up to 9 kBytes.

---

### Post by bernardfrancois on 2009-11-15
What I would do first if I were you, is to search for your network card type in synaptic. Maybe it is available there, and then you don't need to install a driver manually.

If you still want to install this manually, please read on...

As the readme indicates, the first important step is to make sure that you do have one of the listed types of network card.

If you are not sure about it, you'll first have to figure out the exact type of your wireless network card. Then you'll probably have to download a different driver.

Now you need to execute the commands indicated in the readme file. The commands are the lines starting with the #-sign. You need to copy them one by one into a terminal window, but without the #-sign in front.

For example, you start by checking if a certain driver is already installed by executing this:
```
lsmod | grep r8169
```

If the output of that command indicated that this driver was indeed installed, you can remove it by executing the following command:
```
rmmod r8169
```

It's quite well explained what you need to do in this readme file, so you can just follow the instructions there. If you still have any questions, feel free to ask.

---

### Post by Bone Crusher on 2009-11-15
Synaptic does not have it. I am using a Toshiba Satellite A215-S7422 with xubuntu. I downloaded the right driver and it is sitting on my desktop. When I click it there are 3 things in side. Makefile, readme, & src (folder). Inside src there is Makefile, Makefile_linux24x, r8168.h, r8168_asf.c, r8168_asf.h, r8168_n.c, rtl_eeprom.c, & rtl_eeprom.h. I am very new to xubuntu so I have no idea how to do this. When I type the first command, this is what it tells me:

r8169                  34820  0

---

### Post by bernardfrancois on 2009-11-16
Ok, so if you are sure that your wireless network device is in the list on top of the readme, you should follow the instructions in there.

Let me explain the first command:
```
lsmod | grep r8169
```

Actually, there are two commands involved here: **lsmod** and **grep**.

If you would just run 'lsmod', that would give you a list of al installed modules (= drivers). Then, the 'grep' command searches for the text 'r8169' in that list, and it only shows the lines that contain this text.

So when you ran that command, the grep command showed you the line containing r8169. This means this driver is installed.

According to the readme file, you need to uninstall this driver by executing the command listed there:
```
rmmod r8169
```

I would strongly recommend that you carefully read the rest of the readme file and execute the commands.

If you don't feel like reading all of this, you could just give it a try and execute just all the commands (so all the lines with a #-sign in front; but keep in mind that you need to remove the #-sign when you want to execute the command, or it will be ignored).
However, this approach could fail and would require you to come here again and wait for my next reply, so I do recommend to carefully read everything.

If you want to speed things up a bit, and you know how to use IRC, you could also ask your questions in the IRC channel of this forum, so people can help you in real-time.

It's the channel named #ubuntuforums on irc.freenode.org

---

### Post by JBAlaska on 2009-11-16
> **Bone Crusher said:**
> If I have downloaded on my desktop a program, and I open the terminal, which command will install it?

Go to the desktop in a terminal:
```
cd /home/username/Desktop
```

Run this command:
Unpack the tarball :
```
tar vjxf r8168-8.aaa.bb.tar.bz2
```

Change to the directory:
```
cd r8168-8.aaa.bb
```

If you are running the target kernel, then you should be able to do :

```
sudo make clean modules
sudo make install
sudo depmod -a
sudo modprobe r8168
```


Follow the rest of the instructions.

---

### Post by Bone Crusher on 2009-11-17
I tried the first one and this is what it told me:

username@username-laptop:~$ vjxf r8168-8.aaa.bb
bash: vjxf: command not found

tar: r8168-8.aaa.bb.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

When I tried the second one:

username@username-laptop:~$ sudo make clean modules
[sudo] password for username: 
make: *** No rule to make target `clean'.  Stop.
username@username-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
username@username-laptop:~$ sudo depom -a
sudo: depom: command not found
username@username-laptop:~$ sudo modprobe r8168
FATAL: Module r8168 not found.
username@username-laptop:~$

I am pretty sure that this is the right driver.

---

### Post by bernardfrancois on 2009-11-19
When you run the following command, you most likely have to replace aaa and bb by some version numbers.
```
tar vjxf r8168-8.aaa.bb.tar.bz2
```

In other words; one of the files you downloaded has a name similar to r8168-8.aaa.bb.tar.bz2, but with numbers instead of aaa and bbb. You will have to use these numbers instead of aaa and bb in the commands.

---

### Post by Bone Crusher on 2009-11-19
Ah, ok. I still can't get it to work. I am planning on upgrading to ubuntu 9.10. Is it likely I will be able to find and install the wireless drivers more easily with ubuntu 9.10?

---

### Post by Bone Crusher on 2009-11-19
I have just downloaded ubuntu 9.10. It is awesome. It fixed the problem and automatically connected with my wireless network.

---

### Post by bernardfrancois on 2009-11-20
Ok, nice to hear this problem belongs to the past. It's so much easier if drivers are included in the operating system.

Can you mark this thread as solved?

---


---
title: "I got given my first tower! it's headless and I've never dealt something like this."
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by benji5 on 2015-09-26
Hello and thanks for taking time to read my post ill try and make it short and sweet.

Today I got give a Dell Optiples745 SFF I'm not sure if it has been modified but the HDD was 80GB when I put it into my external dock ([URL="https://www.dell.com/downloads/global/products/optix/en/opti_745techspecs.pdf"]https://www.dell.com/downloads/global/products/optix/en/opti_745techspecs.pdf).

[/URL]
I have no tv or monitor to connect it to, I do have a USB keyboard and mouse and two laptops running OSX Yosemite and windows 8.

I want to configure the  HDD externally and ssh into it using my mac but don't have the Dells  IP address or user name/password needed to connect to the heedless server.

I have downloaded 14.04.3 LTS.

Thanks much for any help!

Regards,
Benji

---

### Post by TheFu on 2015-09-26
How do you know it booted?
When/if you installed Ubuntu - did you set a static IP? You should.
When/if you installed ubuntu - did you inntall openssh-server?

Headless servers are all over the place, but usually a monitor/console is mandatory for installation.  You can connect the Mac to the serial port from the server to see the console. Use a terminal program.  38400 baud, 8n1.

---

### Post by QIII on 2015-09-26
You can create an SSH pre-seeded installation DVD/USB, but it should be a Server version with no GUI.  Depending on the tools you have available with your router, you can determine the IP used when the running machine is connected to the router -- many will allow you to assign a static IP from their GUIs.   Then use that IP to SSH.   

It's probably not a trivial thing for someone new to create a pre-seed installation medium.

Using another machine to install Ubuntu Server, adding all the SSH bits and then physically moving the disk may be a quicker solution for a one-off like this, though.

---

### Post by benji5 on 2015-09-26
> How do you know it booted?
When/if you installed Ubuntu - did you set a static IP? You should.
When/if you installed ubuntu - did you inntall openssh-server?
I don't know if the computer boots, all I know about the machine is that it does turn on and the HDD is not corrupt. I dndn't install Ubuntu on the machine yet I wanted to ask here how to properly go about installing and configuring Ubuntu so the machine automatically connects to the internet and start a ssh service/session so I can run ifconfig on my mac and see what IP got assigned to it and use that to connect to it.

I have never installed Ubuntu on a external HDD before or configured a static IP through the CLI and am not very familiar with ssh or how to properly initiate/configure a contention from my mac to my headless server.

> Using another machine to install Ubuntu Server, adding all the SSH bits  and then physically moving the disk may be a quicker solution for a  one-off like this, though.

I was thinking that moving the disk would be easier for me though I would love to learn the pre-seed method of installing a headless server if someone is able to walk me through it.

I could use some instructions on ether or both methods if anyone's willing.

Thanks much!

Regards,
Benji

---


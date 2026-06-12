---
title: "Network Manager w/ two NICs"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by moonguide on 2010-11-01
I put a second NIC in my machine so I can run LTSP. When I try to use the tool provide from the icon in the upper right hand portion of the screen, I get an opportunity to edit the settings for eth0 and eth1. I want to change eth0 from DHCP to static, since I run Apache for my in-house web site. When I apply the change I lose my connection to the Internet. If I change it back to DHCP my connection returns. I've tried running sudo ifconfig eth0 down, and then up, and even though ifconfig shows eth0 as up with 192.168.0.253 for its IP address, I can't get out through my router, which I've told the "Network Connections" tool is 192.168.0.1.

Any thoughts on a reliable way to manage my two NICs in Ubuntu 10.04?

Thanks.

---

### Post by moonguide on 2010-11-02
To use Network Manager on Ubuntu 10.04 to change from DHCP to a static IP address do the following:

Right click on the Network Manager icon -- it's the square with a dot in the middle and a diagonal line running down and to the left from the bottom left corner of the square, and is found in the upper right hand corner of the screen, in my case, to the left of the date and time.

Select "Edit Connections..." from the drop down menu.

Select the appropriate NIC from the list (in the current case, that was shown as Auto eth0) and click on the "Edit..." button.

In the "Editing Auto eth0" dialog click the "IPv4 Settings" tab.

Change "Method" from the "Automatic (DHCP)" entry to the "Manual" entry.

Under "Addresses" click the "Add" button.

Enter the desired address in the "Address" column, the desired netmask in the "Netmask" column, and the gateway address in the "Gateway" column. Be sure to hit the <enter> key after entering the gateway address. If you click away from it, the address disappears. In my example the addresses are:

Address:     192.168.0.253
Netmask:    255.255.255.0
Gateway:    192.168.0.1

Enter the desired DNS server addresses in the "DNS servers:" box, separating each address with a comma. For my example the numbers from Comcast are:

68.87.69.150,68.87.85.102

Enter the desired search domain address in the "Search domains:" box. Again, in my example the search domain from Comcast is:

hsd1.fl.comcast.net

Next, click the "Apply..." button. You will be asked to authenticate by providing your root password.

Finally, to really apply the changes, bring the connection down by clicking (not right clicking) the Network Manager icon and clicking "Disconnect" on the line under the connection you just changed. Then bring the connection back up by clicking the Network Manager icon and clicking on "Auto eth0" or whatever is appropriate for your situation.

---


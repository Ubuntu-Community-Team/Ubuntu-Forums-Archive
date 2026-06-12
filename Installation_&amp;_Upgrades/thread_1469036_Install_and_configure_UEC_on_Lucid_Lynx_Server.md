---
title: "Install and configure UEC on Lucid Lynx Server"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by wcorey on 2010-05-01
Under [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Starting with the following, as this is the node controller

> STEP 3: Install the Node Controller(s)

The node controller install is even simpler. Just make sure that you are connected to the network on which the cloud/cluster controller is already running.

   1. Boot from the same ISO on the node(s)
   2. Select “Install Ubuntu Enterprise Cloud”
   3. It should detect the Cluster and preselect “Node” install for you
   4. Confirm the partitioning scheme
   5. The rest of the installation should proceed uninterrupted; complete the installation and reboot the node 

Steps 1 and 2 were fine. I am not sure it did step 3 as I recall having to specify Node.

The rest went fine.

I get the following:
2010-05-01 21:15:30-04:00 | 19201 -> Calling node cluster1 node 192.168.0.12
2010-05-01 21:15:30-04:00 | 19201 -> Node is not a candidate for local cluster.


Also on the cloud/cluster controller since it is a desktop not a server (but it is 10.4) I manually installed the packages hoping to get prompted through the information in the post install target scripts, which I didn't. but 

Install the eucalyptus-cloud and eucalyptus-cc packages on the Front End:

sudo apt-get install eucalyptus-cloud eucalyptus-cc eucalyptus-walrus eucalyptus-sc

Answer debconf's questions:

    *

      Configure postfix for internet delivery
    * Name your cluster
          o e.g. cluster1 
    * Add a list of available IP addresses on your network
          o e.g. 192.168.1.200-192.168.1.249 

Note: Depending on the number of systems you will be setting up, you may not want to install all the above packages on the same system. For best results, have a look at some recommended topologies. 

These questions never happened and it is not clear how I update the /etc/eucalyptus/eucalyptus-ipaddr.conf.  Specifically,

CC_IP_ADDR="$addr"
WALRUS_IP_ADDR="$addr"
SC_IP_ADDR="$addr"
CLOUD_IP_ADDR="$addr"

The Walrus and Cloud IP address should be a single address but the CC_IP_Addr should be a range? Actually I was about to start an instance back when this all was on 9.10 on two desktops, I don't get anywhere near that far now, so I need some assistance...

Thanks,
Walt

---

### Post by wcorey on 2010-05-09
1) Remove completely all front-end eucalyptus packages
2) apt-get install <front end package>
3) specify cluster1 (or whatever) for cluster name when prompted
4) specify a range, outside of your router's range...i.e. is local host is 168.192.0.nnn specify 168.192.1.nnn-168.192.1.mmmmm

read "Intel Cloud Builder Guide to Cloud Dsign and Deployment on Intel Platforms - Ubuntu Enterprise Cloud

that will fill in missing steps and provide good insight into design.

---


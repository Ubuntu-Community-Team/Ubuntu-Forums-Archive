---
title: "Recommendations for packet sniffing install"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by dschlic1 on 2012-05-04
I would like some recommendations on using a minimal linux installation to be used for ethernet packet sniffing and analysis. I currently use Wireshark running under Windows. It works but has some issues. In particular the standard Windows uses many tasks which produces and recieves packets via the ethernet interface. This results in packets showing up on the capture that need to be ignored.
I use the packet sniffing to debug ethernet communications between different types of industrial equipment. So I do not want the sniffer producing packets of it's own. I think achieving this goal might be easier using Linux than Windows. I might add that I will only be using a wired interface.
I am looking at Ubuntu because I use it at home and am fimiliar with it. So I would like some advice as to how to modify the standard distro (if needed) to eliminate all taks and programs that would send packets via the ethernet interface. I would also like to be able to perform a fast boot off of a CD or a USB flash drive.
This will be installed "on" a Dell M6300 notebook computer.

---

### Post by mips on 2012-05-04
Unlike windows linux does not really 'chatter' on the network unless there is user input. Get something like Xubuntu with a static network config, disable any services and daemons you don't need and the use Remastersys to create your own livecd.

---


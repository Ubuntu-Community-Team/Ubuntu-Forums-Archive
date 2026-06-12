---
title: "Installation problems"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by sisipenzia on 2005-05-18
l was loading ubuntu on my pc and l got to tohe partitioning stage. My pc's hdrive shown a capacity of 20.4gb of free space then l manually set a partition of 1.8gb leaving about 19 gb of space. When l chose to proceed to the next stage a message appeared saying l didn't specify the root type or something, so l chose not to proceed till l knew what l was doing but. l had done all the other required stuff in the partitioning stage. So l switched off the computer and restarted it also removing the intallation disk and a message appeared saying "Operating sysytem not found". How can l restore the state my computer was previously?

---

### Post by Xian on 2005-05-18
[QUOTE=sisipenzia] How can l restore the state my computer was previously?[/QUOTE]
What did you have installed on that HD? Windows? Another Linux OS?

---

### Post by bruizer on 2005-05-18
If you were running Windows previously, you will need resote your MBR (Master Boot Record). Throw in the CD, and go to the recovery console. Use the FIXMBR command... hooefully you still got it! You can also use the FDISK /MBR command... it will rebuild he MBR from the info stored in the partition table.

---

### Post by bruizer on 2005-05-18
It sounds like you got through the partitioning portion of the setup... you may have blasted the partition table [-X

---

### Post by sisipenzia on 2005-05-22
I chose the option to keep the existing information and use it but not to erase the partition I was going to use.

---

### Post by sisipenzia on 2005-05-22
[QUOTE=Xian]What did you have installed on that HD? Windows? Another Linux OS?[/QUOTE]
 I had windows on my hard disk.

---

### Post by sisipenzia on 2005-05-22
[QUOTE=bruizer]It sounds like you got through the partitioning portion of the setup... you may have blasted the partition table [-X[/QUOTE]
 If the partition table may have been blasted, can I still recovery the informaton on the hard disk maybe by making that hard disk a secondary disk and a new one the primary disk so I can access it?

---


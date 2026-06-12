---
title: "Lubuntu 18.04 pxe  halts trying to netboot /mnt/sda1/tftp/images/lubuntu/cdrom"
date: 2019-11-16
forum: Installation &amp; Upgrades
---

### Post by reconfigurator on 2019-11-16
I have set up a pxe server and copies the files over for this distro
client machine starts up    	 	 	 	   [COLOR=#780373][FONT=monospace][COLOR=#000000]everything seems [/COLOR][COLOR=#000000]to go [/COLOR][COLOR=#000000]OK until[/COLOR][/FONT][/COLOR]
  process but halts like this:

  	 	 	 	   [COLOR=#780373][FONT=monospace][COLOR=#000000]trying to netboot 192.168.0.1:[/COLOR][COLOR=#000000]/mnt/sda1/tftp/images/lubuntu/[/COLOR][COLOR=#000000]cdrom[/COLOR][/FONT][/COLOR]
 [COLOR=#780373][FONT=monospace][COLOR=#000000]begin nfs mount -0 nolock 0 ro [/COLOR][COLOR=#000000]192.168.0.1:[/COLOR][COLOR=#000000]/mnt/sda1/tftp/images/lubuntu/  **cdrom** [/COLOR] [/FONT][/COLOR]

 [COLOR=#780373][FONT=monospace][COLOR=#000000]connection refused
[/COLOR][/FONT][/COLOR]
[COLOR=#780373][FONT=monospace][COLOR=#000000]   	 	 	 	  [/COLOR][/FONT][/COLOR]
 [COLOR=#780373][FONT=monospace][COLOR=#000000]Then [/COLOR][/FONT][/COLOR] 

 
 
 [COLOR=#780373][FONT=monospace][COLOR=#000000]Busybox v1.27.2 (Ubuntu 1:1.27.2-2Ubuntu3) built-in shell (ash)[/COLOR][/FONT][/COLOR]
 
 
 [COLOR=#780373][FONT=monospace][COLOR=#000000](initramfs) done.[/COLOR][/FONT][/COLOR]
 [COLOR=#780373][FONT=monospace][COLOR=#000000]Unable to find a live file system on the network[/COLOR][/FONT][/COLOR]
 [COLOR=#780373][FONT=monospace][COLOR=#000000][107.884047] randon: crng init done[/COLOR][/FONT][/COLOR]
 
 
 [COLOR=#780373][FONT=monospace][COLOR=#000000]So something is looking for subdirectory /cdrom [/COLOR][COLOR=#000000]when there isn’t one:

[/COLOR][/FONT][/COLOR]
[COLOR=#780373][FONT=monospace][COLOR=#000000]   	 	 	 	  [/COLOR][/FONT][/COLOR]
 [COLOR=#780373][FONT=monospace][COLOR=#000000]ls -l /mnt/sda1/tftp/images/lubuntu [/COLOR][COLOR=#000000]
-r--r--r--    1 root     root           229 Nov 14 16:42 README.diskdefines 
dr-xr-xr-x    3 root     root          3488 Nov 14 16:29 [/COLOR]**[COLOR=#5454ff]boot[/COLOR]**[COLOR=#000000] [/COLOR][COLOR=#000000]
dr-xr-xr-x    2 root     root          3488 Nov 14 16:42 [/COLOR]**[COLOR=#5454ff]casper[/COLOR]**[COLOR=#000000] [/COLOR][COLOR=#000000]
dr-xr-xr-x    3 root     root          3488 Nov 14 16:42 [/COLOR]**[COLOR=#5454ff]dists[/COLOR]**[COLOR=#000000] [/COLOR][COLOR=#000000]
dr-xr-xr-x    2 root     root          3488 Nov 14 16:42 [/COLOR]**[COLOR=#5454ff]install[/COLOR]**[COLOR=#000000] [/COLOR][COLOR=#000000]
dr-xr-xr-x    2 root     root          8192 Nov 14 16:42 [/COLOR]**[COLOR=#5454ff]isolinux[/COLOR]**[COLOR=#000000] [/COLOR][COLOR=#000000]
-r--r--r--    1 root     root         20664 Nov 14 16:50 md5sum.txt 
dr-xr-xr-x    2 root     root          3488 Nov 14 16:42 [/COLOR]**[COLOR=#5454ff]pics[/COLOR]**[COLOR=#000000] [/COLOR][COLOR=#000000]
dr-xr-xr-x    4 root     root          3488 Nov 14 16:42 [/COLOR]**[COLOR=#5454ff]pool[/COLOR]**[COLOR=#000000] [/COLOR][COLOR=#000000]
dr-xr-xr-x    2 root     root          3488 Nov 14 16:42 [/COLOR]**[COLOR=#5454ff]preseed[/COLOR]**[COLOR=#000000] [/COLOR][COLOR=#000000]
lrwxrwxrwx    1 root     root             1 Nov 14 16:42 [/COLOR]**[COLOR=#54ffff]ubuntu[/COLOR]**[COLOR=#000000] ->

Can someone explain what is happening here please?
Can I solve this by renaming one of the other directories to 'cdrom'?
e.g. isolinux
[/COLOR][/FONT][/COLOR]

  [COLOR=#780373][FONT=monospace][COLOR=#000000][/COLOR][/FONT][/COLOR]
  [COLOR=#780373][FONT=monospace][COLOR=#000000][/COLOR][/FONT][/COLOR]

---


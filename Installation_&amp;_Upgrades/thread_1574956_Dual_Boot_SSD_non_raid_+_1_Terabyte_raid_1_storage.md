---
title: "Dual Boot SSD non raid + 1 Terabyte raid 1 storage = &quot;No Block Device Found&quot;"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by rtrask on 2010-09-15
It's been a real battle, but I am getting close.
I won't go into all the details of the fight that I have had, but I've almost made it to the finish line.

Here is the set up.
ASUS Z8PE-D18 mother board 2 CPU, 8 Gig Ram
I recently added an OCZ Agility SSD, defined a raid 1 virtual disk on the 1 terabyte WD HDD drives, which will holds all of my user data, the SSD is for executables. The bios is set to AHCI.

Windows 7 installed fine, recognizes the raid VD just fine. 

I installed Ubuntu 10.04 by first booting into try and mode, then opening a terminal and issuing a "sudo dmraid -ay" command. Then performing the install. I told it to install the raid components, and told it to let me specify the partitions manually. When setting up the partitions, I told it to use the free space I set aside on the SSD from the Windows 7 install as ext4 and to mount root there. Ubuntu installed just fine, grub2 comes up just fine, and Windows 7 boots with out a hitch, recognizing the mirrored partition as I indicated previously.  When I tell grub to boot linux however, it pauses and I get the "no block devices found" message. It will then boot, but it does not recognize the raid array. After Ubuntu starts up I can run "dmraid -ay" and it recognizes the raid array, but shows the two component disks of the raid array as well. It will not allow the component disks to be mounted, but they show up which is annoying. (I can live with that if I have to)

I have fixed a similar problem before by setting up a dmraid script in /etc/initramfs-tools/scripts/local-top ... following the instructions found at the bottom of this blog:

[http://geertjohan.riemer.nl/2010/05/06/installing-kubuntu-with-dmraid/](http://geertjohan.riemer.nl/2010/05/06/installing-kubuntu-with-dmraid/) 

To recap: My problem is that after grub2 fires up Ubuntu 10.04.1 LTS (Lucid Lynx), it pauses, and I get "no block devices found" It then boots but does not recognize the raid array untill I manually run "dmraid -ay". I've hunted around for what to do but I have not found anything. It may be some timing issue or something, but I am so tired of beating my head against this wall. ](*,)

I need some help.

Any kind soul out there ?

---

### Post by ronparent on 2010-09-15
Unfortunately how raid is handled has been in transition and varies from version to version. We need to know what Ubuntu version you have installed. Also it would be helpful if you could download the Boot Info Script, run it and post the results. The script can be found here: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

---

### Post by rtrask on 2010-09-15
OK, I ran the script, and I have attached the results file. I don't see anything that I that I think indicates an error. 

just for grins, I ran it a second time after first running the command "dmraid -ay" the results were the same except for the following diff:


rtrask@JOB-42-2:~/Downloads$ vi RESULTS1.txt
rtrask@JOB-42-2:~/Downloads$ diff RESULTS1.txt RESULTS.txt 
188,194d187
< =============================== "ls -R /dev/mapper/" output: ===============================
< /dev/mapper:
< control
< ddf1_4c53492020202020808627c3000000004711471100001450
< ddf1_4c53492020202020808627c30000000047114711000014501
< ddf1_4c53492020202020808627c30000000047114711000014505
< 

Some details that I left out on the original post.
I had initially created a swap partition on the mirrored drive The install had an issue mounting it so I told it to continue with out a swap partition. With 8 Gig of ram, I figured I would be fine with that until I could manually deal with the swap partition later.

Also I added a custom menu item to gub2 so that Windows occurs bot first and last in the grub menu because I did not disable grub's search for other OS.

---

### Post by ronparent on 2010-09-15
To connect with 10.04 on a raid, the boot sector has to be written to the raid root. You haven't said what raid level you are using - my guess would be 1. I don't recognize the /dev/mapper raid partition terminology at all. Is the  ddf1_ddf1_4c53492020202020808627c3000000004711471100001 450 the overall raid and the following two the partitions? 

See  this reference for reinstalling grub: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

It appears that for using method 1 in a terminal on a live cd you would have to mount the ddf1_....4501 partition to /mnt.  The ddf1_.....450 partition would then be the target for install-grub to install the boot loader. I would cut and paste the following commands:

> sudo mount /dev/mappwr/ddf1_4c53492020202020808627c3000000004711471100001 4501 /mnt

And then:

> sudo grub-install --root-directory=/mnt/ /dev/mappwr/ddf1_4c53492020202020808627c3000000004711471100001 450

Let us know how it turns out.:D

---

### Post by rtrask on 2010-09-16
ronparent, thanks so much for all of your help.

You are correct it is raid 1. 
My understanding from experience is that ddf1_4c53492020202020808627c3000000004711471100001450 is the over all raid, and ddf1_4c53492020202020808627c30000000047114711000014501 is the (at this point unused swap partition, and that ddf1_4c53492020202020808627c30000000047114711000014505 is the ntfs formatted storage partition.


I'm a bit confused by what you are suggesting. 

Currently when booting linux initramfs loads, but for some reason is unable to initialize the raid array with "dmraid -ay" if I move grub to the raid array, that implies that "dmraid -ay" .. or the equivalent has already executed to start the raid array. What will do that, and why is it not already doing it?

I'm willing to try what you have suggested, but I would like to have a back out plan before I do. I think that that my back out plan would be something like:

1 boot with the alternate CD
2 go down the fix a broken system path, and execute a shell on the current sda3 partition.
3 then execute the equivalent mount & grub install commands for sda3 & sda.


Remember, I do not want the executables on on the raid array. I want them on the SSD. I am close to what I want, but I don't understand why the raid array is not being initialized by Linux, but is by windows. After Linux boots, the raid array initializes just fine by executing the "dmraid -ay" command. 

It seems to me that the problem I am having could most easily be fixed by tweaking the initramfs configuration. Or the fault is with the bios, and I am just screwed until they come out with a patch for it.

---


---
title: "unable to load ubuntu after installation  (dual-boot)"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by javanoob on 2012-06-06
hi guys,

I am on a dual boot system with both window 7 and ubuntu running together.
The harddisk are partitioned in this way

sda1,2,3 - windows related partition
sda5 - /boot
sda6 - swap
sda7 - /
sda8 - /home

For the boot loader installation, i choose sda5 under the /boot folder

--------------------------------------------
However, after installation completes, i am prompt to take out the cd and restart but i still get booted into windows 7.
--------------------------------------------

q1) when we create the /boot partition, is GRUB is not included ? what actually does /boot does ? what does it actually contain ?

q2) for the bootloader installation, is it GRUB installation ?

q3) i am guessing that i am not able to boot into ubuntu because i did not install the bootloader in the MBR portion in the 1st sector of harddisk ?

am i right ? but where n how do i determine where is the 1st sector of the harddisk ?

q4) i understand that GRUB installation has a few layer. 
layer 1 will make changes to the MBR
layer 2 will read the boot sector of the partition containing the grub.conf ?
layer 3 will load the kernel

am i right ? so when installing grub , will grub put's it grub.conf in  /boot? or it will put the grub.conf in whatever partition i choose to  install my bootloader ? 

q5) can someone point out what is the relation between bootloader and /boot and MBR(1st sector of hdd)

if i install my grub in the 1st sector of my hdd, where will my grub.conf goes to ?

q6) where did i got it wrong and what should i actually do next ?

:(

Look forward to the forum's advices. ):P

Regards,
Noob

---

### Post by carl4926 on 2012-06-06
If you use a /boot
You need to have the bootflag on it and during install you have to select it for Grub, default is sda, but you have use the drop down and select sda5 (in your case)
[http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg](http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg)

---

### Post by javanoob on 2012-06-06
> **carl4926 said:**
> If you use a /boot
You need to have the bootflag on it and during install you have to select it for Grub, default is sda, but you have use the drop down and select sda5 (in your case)
[http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg](http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg)


Hi carl4926, 

The problem is I have selected sda5 (/boot) for the installation of the boot loaader but i still cannot boot into ubuntu, going directly into win7.

It seems like the MBR is not updated.
So how do i install bootloader into /sda and updating the MBR as well ?

Regards,
Noob

---

### Post by wilee-nilee on 2012-06-06
You don't need a boot partition, it is just making the set up more complex than it needs to be, hence this problem.

See next post for the fix.

---

### Post by darkod on 2012-06-06
Your mistake was to choose sda5 for bootloader installation. The bootloader goes to the MBR because that's where the boot process starts. In other words to /dev/sda, without any number.

You can boot into live mode with the cd and add grub2 to the MBR with:
```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

That should install grub2 to /dev/sda.

If that doesn't work, sometimes the last command needs to be modified as:
```
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by javanoob on 2012-06-06
> **darkod said:**
> Your mistake was to choose sda5 for bootloader installation. The bootloader goes to the MBR because that's where the boot process starts. In other words to /dev/sda, without any number.

You can boot into live mode with the cd and add grub2 to the MBR with:
```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```That should install grub2 to /dev/sda.

If that doesn't work, sometimes the last command needs to be modified as:
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Hi Wilee and Darko, 

Thanks for the reply.
I am very curious what does the /boot partition actually does ? 

I have seen people installing grub into /boot thus i am following the way they did it without actually knowing why.

Does the /boot partition actually contain the kernel ? 
I have read examples and they mentioned layer 2 grub store their .conf file inside /boot while the layer1 changes the codes in the MBR.

So i am confuse, how do we install the bootloader in MBR and yet have the .conf files in /boot ?

Nevertheless i am trying your way now. Will update asap.

Regards,
Noob

---

### Post by darkod on 2012-06-06
If you have a separate /boot partition, or if it's only a boot folder inside your / partition, the role is the same.

Yes, it holds the kernel and the grub configuration files. Grub installs only small part on the MBR (because there is no space for all of it), and then knows where to look for the rest of the files.

If you install grub to a partition like you did, you need to tell windows bootloader which is then left on the MBR to find it and call it. It's often much more complicated, so the it's usually best to install grub on the MBR and let it boot both OSs (windows bootloader can boot only windows by default).

Exception of this rule is if you have some important reason to keep windows bootloader on the MBR, but in 99% cases it's best to just install grub to the MBR.

---

### Post by javanoob on 2012-06-06
> **darkod said:**
> If you have a separate /boot partition, or if it's only a boot folder inside your / partition, the role is the same.

Yes, it holds the kernel and the grub configuration files. Grub installs only small part on the MBR (because there is no space for all of it), and then knows where to look for the rest of the files.

If you install grub to a partition like you did, you need to tell windows bootloader which is then left on the MBR to find it and call it. It's often much more complicated, so the it's usually best to install grub on the MBR and let it boot both OSs (windows bootloader can boot only windows by default).

Exception of this rule is if you have some important reason to keep windows bootloader on the MBR, but in 99% cases it's best to just install grub to the MBR.

Hey darko! 
Thanks for the explanation.

Just to clear things up alittle. 
By installing grub on the sda (MBR), will it still install the .conf on the /boot partition ?

Regards,
Noob

---

### Post by javanoob on 2012-06-06
> **javanoob said:**
> Hi Wilee and Darko, 

Thanks for the reply.
I am very curious what does the /boot partition actually does ? 

I have seen people installing grub into /boot thus i am following the way they did it without actually knowing why.

Does the /boot partition actually contain the kernel ? 
I have read examples and they mentioned layer 2 grub store their .conf file inside /boot while the layer1 changes the codes in the MBR.

So i am confuse, how do we install the bootloader in MBR and yet have the .conf files in /boot ?

Nevertheless i am trying your way now. Will update asap.

Regards,
Noob

Hey darko, 

Thanks. I am inside Ubuntu now!

Can you shed somelight on this 
sudo grub-install --boot-directory=/mnt/boot /dev/sda
What it actually does ?
How does system know where grub-install is ? 
What does the parameter --boot-directory means ? (try to man it, but only saw root-directory)

Thanks alot.
Really appreciate it so haappy now~

Rgds,
Noob

---

### Post by dino99 on 2012-06-06
Glad you succeed ):P

"sudo grub-install --boot-directory=/mnt/boot /dev/sda "

thats means:
- choose the boot partition and set the boot flag on /dev/sda , aka the mbr

more info via the links below, good luck :guitar:

---

### Post by javanoob on 2012-06-06
> **dino99 said:**
> Glad you succeed ):P

"sudo grub-install --boot-directory=/mnt/boot /dev/sda "

thats means:
- choose the boot partition and set the boot flag on /dev/sda , aka the mbr

more info via the links below, good luck :guitar:
Hi dino,
Thanks for the reply!

I assume the boot partition = /mnt/boot and the bootflag is on /dev/sda ? am i right ?
so what will grub actually do ?

re-write the MBR code in the /dev/sda to point to /mnt/boot ?

Regards,
Alan

---

### Post by darkod on 2012-06-06
sudo grub-install <destination>

tells it where to install the starting part of grub2. But since you are doing it from live mode, it doesn't really know where your installed system is, so you need to mount it first on a temporary mount point (like /mnt) and you need to use the --boot-directory parameter telling it where is the /boot partition mounted.

If you don't have a separate /boot partition, you mount only the root at /mnt and use the --root-directory option.

That installs grub2 to the MBR but doesn't touch your boot flag specifically. The boot flag should stay on your windows partition.

---


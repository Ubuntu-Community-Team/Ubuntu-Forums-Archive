---
title: "Re-Install without wiping all of HDD"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by Rixsta on 2012-11-25
Hi, I have a ubuntu 11.10 Server that has a single 1TB HDD , the machine is not here in England but is in france on a Kimsufi server, i feel like some  time soon i would like to reinstall the linux operating system. 


/dev/sda1  ext4  /          9.76GB    Boot
/dev/sda2  ext4 /home    921GB 
/dev/sda3 linux-swap      511MB    

however i want to keep the data on the sda2, so is this possible to re-install without wiping that drive ? i have nowhere to back the data up to.

home is where i keep all my data!         

any help apreciated!

---

### Post by darkod on 2012-11-25
Yes, you can. Use manual partitioning, and after selecting the /home partition in the Use As select the same ext4 filesystem, the mount point /home and make sure you DO NOT select the format option.
You will need to create the same first user as you did last time. You can create the other users after the OS is installed.

---

### Post by Rixsta on 2012-11-25
Thankyou, i think that would work in most cases as i can see now however i just found out my options in the control panel for re-installing are

You have chosen to install **ubuntu1110-server**. 

We propose the following layout of partitions:            

.Default layout of partitions for distributions ubuntu1110-server    
.The same layout of partitions as before    
.Personalized layout of partitions
            
Attention, this operation will result in all data being deleted from the hard disk!         

which ever one i choose it seems it will wipe the disk. oh well must be because they want you to upgrade and buy extra drive.

---

### Post by darkod on 2012-11-25
Since this is a hosted service they might have applied limitations. You better discuss it with the provider.

---

### Post by pkadeel on 2012-11-25
> **Rixsta said:**
> Thankyou, i think that would work in most cases as i can see now however i just found out my options in the control panel for re-installing are

You have chosen to install **ubuntu1110-server**. 

We propose the following layout of partitions:            

.Default layout of partitions for distributions ubuntu1110-server    
.The same layout of partitions as before    
.Personalized layout of partitions
            
Attention, this operation will result in all data being deleted from the hard disk!         

which ever one i choose it seems it will wipe the disk. oh well must be because they want you to upgrade and buy extra drive.
I think "Personalized layout of partitions" option will give you an option to mount your /home without formating. Additionally as the option name implies, it should not fire up the installation right away. Instead it will present you another set of options or a partition tool which you shall be able to cancel if your required feature is not present there.

---


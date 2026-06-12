---
title: "Ubuntu won't boot"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by chenr1 on 2011-11-13
Hey guy's I've been using Ubuntu for about a month know. Heres the problem: I have a Dell Poweredge 2450 Server right know I have it on windows 2000 server. Since i run a minecraft server(not important though) I decided to move the server onto ubuntu. Considering I already have ubuntu on my Desktop and Laptop. I'm attempting to load desktop version becuase i have actually tested to make sure the software work's on the desktop version. I have a Cd that i've used for other computers that countains the iso. I cant boot from disk on the server because the server has disk drive problem. Hey guy's I've been using Ubuntu for about a month know. Heres the problem: I have a Dell Poweredge 2450 Server right know I have it on windows 2000 server. Since i run a minecraft server(not important though) I decided to move the server onto ubuntu. Considering I already have ubuntu on my Desktop and Laptop. I'm attempting to load desktop version becuase i have actually tested to make sure the software work's on the desktop version. I have a Cd that i've used for other computers that countains the iso. I cant boot from disk on the server because the server has disk drive problem.    So I downloaded the wubi installer (which i used on my laptop) and ran it but halfway through the install it gets some error. So I went and got and external disk drive that happens to be usb so i cant boot from disk. But when i log into windows im able to click the external drive and it has those three selections i choose install ubuntu alongside windows.   THIS IS WHERE I THINK THE PROBLEM STARTS: I have two hard drives on this server one nine GB the other about 40GB windows is on the 9GB so I installed ubuntu on the empty 40GB hard drive. Which doesnt have anything on it.  This way the wubi installer works correctly and when it restarts the computer ubuntu finishes installing.    So I downloaded the wubi installer (which i used on m laptop) and ran it but halfway through the install it gets some error. So I went and got and external disk drive that happens to be usb so i cant boot from disk. But when i log into windows im able to open the wubi installer and start the wubi.exe   THIS IS WHERE I THINK THE PROBLEM STARTS: I have two hard drives on this server one nine GB the other about 40GB windows is on the 9GB so I installed ubuntu on the empty 40GB hardrive. So  when ubuntu is finished installing using wubi it restarts the computer and continues installing. After it's totally finished restarting it restarts again and at this point when i choose ubuntu as the os. I am taken to the Grub menu and i chose the first one. And as soon as i choose this the screen turns purple and just sits...  Please Help.

---

### Post by Neill_R on 2011-11-13
What happens if you try the second grub option What version of Ubuntu are you using?

---

### Post by chenr1 on 2011-11-14
By the second option do you mean recovery mode? If I select recovery mode it stops at loading initial ramdisk. And I am on ubuntu 11.10 I believe.

---

### Post by darkod on 2011-11-14
Any particular reason to use wubi and not a proper install?

---

### Post by chenr1 on 2011-11-15
> **darkod said:**
> Any particular reason to use wubi and not a proper install?

The disk drive doesn't work. And it won't boot from external Which I have.

---

### Post by thomas07vt on 2011-11-15
> The disk drive doesn't work. And it won't boot from external Which I have. 
 
what about booting from a flash drive?

---

### Post by chenr1 on 2011-11-15
the only problem from booting from a flash drive is that this server is kinda old. And i dont think bios boots from a flash drive on this system. Because bios doesnt even recognize a usb keyboard.

---

### Post by collisionystm on 2011-11-15
> **chenr1 said:**
> Hey guy's I've been using Ubuntu for about a month know. Heres the problem: I have a Dell Poweredge 2450 Server right know I have it on windows 2000 server. Since i run a minecraft server(not important though) I decided to move the server onto ubuntu. Considering I already have ubuntu on my Desktop and Laptop. I'm attempting to load desktop version becuase i have actually tested to make sure the software work's on the desktop version. I have a Cd that i've used for other computers that countains the iso. I cant boot from disk on the server because the server has disk drive problem. Hey guy's I've been using Ubuntu for about a month know. Heres the problem: I have a Dell Poweredge 2450 Server right know I have it on windows 2000 server. Since i run a minecraft server(not important though) I decided to move the server onto ubuntu. Considering I already have ubuntu on my Desktop and Laptop. I'm attempting to load desktop version becuase i have actually tested to make sure the software work's on the desktop version. I have a Cd that i've used for other computers that countains the iso. I cant boot from disk on the server because the server has disk drive problem.    So I downloaded the wubi installer (which i used on my laptop) and ran it but halfway through the install it gets some error. So I went and got and external disk drive that happens to be usb so i cant boot from disk. But when i log into windows im able to click the external drive and it has those three selections i choose install ubuntu alongside windows.   THIS IS WHERE I THINK THE PROBLEM STARTS: I have two hard drives on this server one nine GB the other about 40GB windows is on the 9GB so I installed ubuntu on the empty 40GB hard drive. Which doesnt have anything on it.  This way the wubi installer works correctly and when it restarts the computer ubuntu finishes installing.    So I downloaded the wubi installer (which i used on m laptop) and ran it but halfway through the install it gets some error. So I went and got and external disk drive that happens to be usb so i cant boot from disk. But when i log into windows im able to open the wubi installer and start the wubi.exe   THIS IS WHERE I THINK THE PROBLEM STARTS: I have two hard drives on this server one nine GB the other about 40GB windows is on the 9GB so I installed ubuntu on the empty 40GB hardrive. So  when ubuntu is finished installing using wubi it restarts the computer and continues installing. After it's totally finished restarting it restarts again and at this point when i choose ubuntu as the os. I am taken to the Grub menu and i chose the first one. And as soon as i choose this the screen turns purple and just sits...  Please Help.


Remove your 9GB Windows drive.
Install Ubuntu with regular install on the 40GB drive.

Once ubuntu is installed, power off, re install Windows drive. 
Grub2 should automatically recognize windows, if not, you can look up how to add it to your grub manually.

---

### Post by chenr1 on 2011-11-15
I Cant do it from reagular install because the disk drive doesnt work.

---

### Post by collisionystm on 2011-11-15
> **chenr1 said:**
> I Cant do it from reagular install because the disk drive doesnt work.


Ah... and you cant boot from usb either. Gotcha.

I do not know how creative you are feeling, but I would give this a shot.
[http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html](http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html)

---

### Post by chenr1 on 2011-11-15
Any suggestions?

---

### Post by collisionystm on 2011-11-15
> **chenr1 said:**
> Any suggestions?

yeah put your 40gb drive in a working machine and load ubuntu then put back into server.

---

### Post by chenr1 on 2011-11-15
Great Idea!!!!! I will look into that. Thanks for being so helpfull guys,

---


---
title: "ata1 and ata2 errors for 7.10 server install"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by metaphorz on 2008-01-14
I obtained errors when installing the Server 7.10 on a new
machine. here is the sequence of events:

Machine: Dell Vostro 400
contains 2 SATA disks
4GB memory

1. Installed the server using the "entire disk" option without LVM
2. Everything proceeded without problems until it asked me to remove
    the server CD to reboot the system.
3. The following status lines were issued:

IRQ18: nobody cared (try booting with he "irqpoll" option
Disabling IRQ18
ata1.00: failed to set xfer mode (err_mask=0x40)
...a few of these...
ata2.00: failed to set xfer mode (err_mask=-x40)
...a few of these...
[<f8891670>] (usb_hcd_irq+0x0/0x60 [usbcore])

Then it rebooted (again) and no errors occur and I am
able to log in to the server using the username and password
that I specified. I am unable to log in as root as I do not
recall any installation procedure that asked me to provide
a root password.

Two questions:

(1) Should be above set of errors require a test or change
    of some kind?

(2) Is there a clean way to set the root password on the
     server?

-p

---

### Post by Partyboi2 on 2008-01-15
I don't use the server version, but I would think this would work the same, if not I am sure someone will correct me :)
When you boot the system you will see something like "grub loading" press "Esc" which will take you to grub menu and then highlight the kernel you are booting into and press "e" to edit, then highlight the line starting with "Kernel" and press "e" again and at the end of the line add 
```
irqpoll
```This lasts for one boot to make this perm. You will need to add it to grub menu.lst  should this work. 
Once you are logged in, In the terminal you would type
```
sudo nano /boot/grub/menu.lst
```look for a section like this:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro[/COLOR]at the end of the line I have highlighted you would add ```
irqpoll
```so it will look something like this:
```
# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro irqpoll
```then save Ctrl+O then exit Ctrl+X
then update grub
```
sudo update-grub
```As for the root you would use sudo in front of a command to give you root permissions and the password is the password you use to login. You can read more here
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by metaphorz on 2008-01-15
First off, I would like to thank you for your unusually lucid and complete explanation. I have made the modification that you suggested for the ata0,1,2.. errors and rebooted 3 times
in succession without an issue. Before, a fresh boot
would work about 30% of the time on the first boot, so while it is not certain that this change has fixed
the problem, things look good so far! I suppose that I am going to have to read up on the 
"irqpoll" option to see what this is doing.

With regard to the second question, there seems to be a problem in doing a 7.10 Server install
as far as setting root password. The main issue is that sudo does not work either since I was
not in the "sudoers" list. One would think that installing the 7.10 server, and providing a username
and password, would have placed my username in the sudoers list. But it did not. The way 
around this was to boot into grub and use the "recovery mode" option. By using this, I
was dumped into root and was able to use visudo to place my username just after "root" in
that file.

For completion for this thread, on the server install, there were two other issues there
were resolved:

1) My username was not set up as a system administrator. I have Gnome, and noticed
that under System->Administration there were very few entries. This problem seems consistent with
   the sudoers issue above. To resolve it, I had to run users-admin and then add "Administer System"
to my username's list of capabilities.  

2) The DNS address was not set up correctly as the DNS lookup for me is on another machine.
"dnslookup" didn't work. So, there was a self-referencing IP (localhost I think)
 in /etc/resolve.conf which had
to be hand-edited to put down the correct IPs for the DNS servers. After that, DNS
worked.

All in all, there seem to be a few warts with the 7.10 installation but so far they are not
insurmountable.

---


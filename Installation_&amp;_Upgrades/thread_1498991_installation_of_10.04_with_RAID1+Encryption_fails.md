---
title: "installation of 10.04 with RAID1+Encryption fails"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by jomex on 2010-06-01
i just tried to install with Ubuntu 10.04 AMD64 Alternate on RAID1 and Encryption but after reboot the screen just stays black.

my system is a AMD Athlon 64 X2 Dual Core 4200+ on a Abit AN-M2HD   Motherboard, and 2 HDs each 250.1 GB
i split the HD into
* 50GB for /
* 200GB for /home
* 1GB for swap
all get a RAID1
/home is encrypted with passphrase (Twofish 256, cbc-essiv:sha256)
swap is encrypted with random (Blowfish 128, cbc-essiv:sha256)

any suggestions?
is this a known issue?
where can i check RAID and hardware compatibility?

---

### Post by jomex on 2010-06-01
the partition table in the installer looks like:
```

SCSI5 (0,0,0) SDA 250.1GB ATA ST3250310AS
    #1 primary 49.0 GB B raid
    #2 primary 200.0 GB  raid
    #3 primary 1.1 GB  raid
SCSI7 (0,0,0) SDA 250.1GB ATA ST3250310AS
    #1 primary 49.0 GB B raid
    #2 primary 200.0 GB  raid
     #3 primary 1.1 GB  raid
 RAID1 device #0 49.0 GB unknown <-- unknown?
     #1 49.0 GB ext4 /
 RAID1 device #1 200.0 GB Software RAID device
       #1 200.0 GB crypto (with phrase)
RAID1 device #2 1.1 GB Software RAID device
      #1 1.1 GB crypto (random)
Encrypted volume (md1_crypt)
    #1 200.0 GB ext4 /home
Encrypted volume (md2_crypt)
    #1 1.1 GB swap swap

```i similar configuration worked with Ubuntu 9.10 Alternate AMD64
the only difference was that the uncrypted disk was just /boot, and a RAID0, so was swap

---

### Post by acrazyplayer on 2010-06-01
Maybe if you try narrowing it down to one cause or the other. For example try installing without encryption and see if it works fine. Then try without RAID and see how that works. I had a problem before with encryption so I just forgot about it but that was a few releases ago. On the Known Issues of Ubuntu 10.04 it says Encrypted partitions must be listed in /etc/fstab

"Users who have configured any encrypted partitions in /etc/crypttab to start at boot time (i.e., not using the noauto option) should make sure that the filesystems on these volumes are listed in /etc/fstab. Otherwise, the passphrase prompt is not guaranteed to be displayed at boot time." 

But I dont think thats your problem

---

### Post by jomex on 2010-06-01
removed by author

---

### Post by jomex on 2010-06-01
i just installed Ubuntu 10.04 AMD64 Desktop and Alternate with "entire disk" option and it works.
it's strange though that alternate installation takes much much longer.
*trying RAID1 without encryption now*

---

### Post by acrazyplayer on 2010-06-01
To make the installation go a little faster then unplug your computer from the internet. It wont download anything like language packs or security updates, all of which you can do after the installation.

---

### Post by jomex on 2010-06-01
RAID only is working
Encryption only is NOT, i get the [error: no such disk-error](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

what's strange though:
when i boot from SATA1 (system) grub is showing the above error
when i boot from SATA2 (empty) the screen stays black and the monitor goes to standby... which is the same error i get when i do RAID+Encryption booting from any disk.

(...and i hate the alternate installer :mad:)

> acrazyplayer
 thx for the advice!

---

### Post by acrazyplayer on 2010-06-01
Ok well since encryption is killing you here depending on what you want encrypted you may be able to set that up after installation of Ubuntu with RAID+1. I just found a few tuts explaining how to set up a non-encrypted home folder into a encrypted one. However you may want *everything* encrypted and I'm not sure you can do that after a normal install.

---

### Post by jomex on 2010-06-01
>> [error: no such disk-error]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")
> If you were not able to boot into  you OS,   you are  infected by a  different problem and should not continue this howto.

i wasn't able to boot into the OS after deleting the specified line. i assume it's a grub MBR left over from another installation.

> depending on what you want encrypted

just my user home directory actually...
what i need is secure and transparent encryption on my whole home folder but i just want to enter the encryption phrase only once (passphrase is very long)

---

### Post by jomex on 2010-06-01
i just test the home directory encryption on a quick Desktop installation, thanks for the hint!
something i found rather odd however: why do i need to enter a passphrase to setup encryption and why can the home directory be access by me just entering the login phrase... isn't that insecure?

---

### Post by acrazyplayer on 2010-06-02
Well if it did then anyone could easily change your password by logging in as root, or with a livecd, or in recovery mode, soooooooo it would be best to have the encrypted partition use a different way of unencrypting itself.

---

### Post by jomex on 2010-06-02
erm... so home encryption does give a false impression of security?

when i enter my login password (10chars) it seems the computer has access to the plain passphrase (which i got asked for on first login) which in turn unencrypts the home directory. thus my encryption is only 10chars strong?
i know everyone can mess with my system if he has physical access to it, but if the computer gets stolen my files are at least encrypted. in this case only weakly though.

---

### Post by acrazyplayer on 2010-06-02
You seam to understand. The encryption will never be cracked in very long time but the password however can. As long as you have a decent password with different characters then even that would take awhile to crack. it goes something like this, you choose 10 characters from a total of 94 (give or take) to form your password. 

So lets say they find out its ten characters long so they set there machine to try and crack it. That machine has to try 94 different times just for a 1 character password. So a 2 character password would have 8836 combinations to crack. Then so on until your 10 character password which would take 53861511409489970176 guesses with one of them being your password. lol However though people often profile you. This means they find out what they can about anything that has any special interest to you. Like your mothers maiden name, your high school, your partners full name, kids, address, what sports you like and so on until they can basically just guess what you would use for your password. They also can do things like "they like the Chicago Bears, but we tried that so lets try "ch1c4g08*4rsR#1"" This would be significantly faster then brute forcing a password. 

Sorry for the long essay, but very long story short, if your password is something guessable then change it to something completely random, do not use that password for anything else, and never tell anybody it and you can enjoy a nice secure encrypted computer.

---

### Post by jomex on 2010-06-03
i know. but why do i have to enter a passphrase on first boot for home directory encryption? login password => decrypts passphrase => decrypts home directory, thus the passphrase is useless.

---

### Post by acrazyplayer on 2010-06-03
Well you could try this. change your user password by typing "sudo passwd user" insert your user name where it says user. then type in some different password and reboot. when it goes to log you in *hopefully* it either asks for 2 passwords or the /home will not be decrypted. both would be good considering no one would be able to get into it without knowing your original password. However if the /home is decrypted with the new password then it all does seam a little worthless...

Oh and if something goes wrong then simply change your password back by doing the same steps as above.

---

### Post by jomex on 2010-06-03
good idea.
i just did that and i get full access to the home directory by only entering the login password.

---

### Post by jomex on 2010-06-03
i just generated a new user with home encryption and it turns out that i entered the wrong password at "Home Encryption -> Run This Action Now" which left me with no error message and also no randomkey.
i think the home encryption is done on the whole home directory (contrary to what the wiki says), the password is just the user login (=> weak) and there is no second password after all.

thanks for all your help [acrazyplayer]("http://ubuntuforums.org/member.php?u=1085274")

i think when i use a strong password for my user and create a separate super-user with a weak password i should get what i want:
* strong encryption on home
* long password at login
* short password for su

---


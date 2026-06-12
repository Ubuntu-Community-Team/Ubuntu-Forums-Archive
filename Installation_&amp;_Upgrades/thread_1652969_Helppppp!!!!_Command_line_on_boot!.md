---
title: "Helppppp!!!! Command line on boot!"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by pinnacle65 on 2010-12-26
Ok so i havent used my ubuntu in a while. Im dual boot. So i decide to boot into ubuntu and I get this screen? Wtf?

---

### Post by amsterdamharu on 2010-12-26
Could you boot from a live CD and post the results of the [boot info script]("http://sourceforge.net/projects/bootinfoscript/")?

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by pinnacle65 on 2010-12-26
> **amsterdamharu said:**
> Could you boot from a live CD and post the results of the [boot info script]("http://sourceforge.net/projects/bootinfoscript/")?

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)



Here you go [http://www.rapidspread.com/file.jsp?id=ffjhmmxd6y](http://www.rapidspread.com/file.jsp?id=ffjhmmxd6y)
the site didnt let me post the log here for some reason. I uploaded the log in a notepad kind of file there!  Helppp!! I need to use my pc!! :(

---

### Post by amsterdamharu on 2010-12-26
The file won't download there, sorry.

Could you use the "Manage attachment" button below a new reply and upload it.

Or copy and paste the text in a new reply with code tags?

---

### Post by aeroaishik on 2010-12-26
Did you delete any files? Seems to me that you deleted some important root files and thus this is hapenning. Try to install Ubuntu again and then see what happens.

---

### Post by fatal_ERROR777 on 2010-12-26
It looks like you moved some system files, or you have a super rare virus installed. The best solution is to install a newer version of ubuntu, because they have an improved security.

Fatal_Error

---

### Post by amsterdamharu on 2010-12-26
> **aeroaishik said:**
> [SIZE=1]Did you delete any files? Seems to me that you deleted some important root files and thus this is hapenning. Try to install Ubuntu again and then see what happens.[/SIZE]

That would be a good suggestion if the OP doesn't mind potentially loosing all the personal files on his computer. We don't know if he has a separate partition for home directory.

I am not sure if you choose during partitioning not to format that the home folder is going to be untouched.

---

### Post by amsterdamharu on 2010-12-26
> you have a super rare virus installed

Sure, that would be the first for me in using Fedora and Ubuntu in about 4 years.

The only virus I came across so far are called [PEBCAK and PICNIC]("http://en.wikipedia.org/wiki/User_error")

---

### Post by pinnacle65 on 2010-12-26
> **fatal_ERROR777 said:**
> It looks like you moved some system files, or you have a super rare virus installed. The best solution is to install a newer version of ubuntu, because they have an improved security.

Fatal_Error


I didnt do anything at all. THe only thing i had installed was ubuntu 10.10. How could this have happened?

---

### Post by dino99 on 2010-12-26
your screenshot shows a kernel panic (its not so rare :()

so reboot or 

try "recovery mode", then "repair packages", then "continue normal boot"

or boot either with: noacpi, nomodeset on the boot line (remove "quiet splash" to let you know what happens behind the scene)

---

### Post by pinnacle65 on 2010-12-26
Maybe im doing this all WRONG!!! can you guys please explain to me how to use the boot_info_script055.sh  file?  I download it and then what?!

---

### Post by Rubi1200 on 2010-12-26
If you are on the LiveCD, you download the file and then move it to the Desktop.

Open a terminal from Applications > Accessories, and paste the following command:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will generate a file on the Desktop called RESULTS.txt

Open it and copy/paste the contents.

Post it back here.

When you click on new post you will see the # symbol on the menu.

Click on this and paste the contents between the tags.

Submit and done.

---

### Post by pinnacle65 on 2010-12-26
> **Rubi1200 said:**
> If you are on the LiveCD, you download the file and then move it to the Desktop.

Open a terminal from Applications > Accessories, and paste the following command:
```
sudo bash ~/Desktop/boot_info_script*.sh
```This will generate a file on the Desktop called RESULTS.txt

Open it and copy/paste the contents.

Post it back here.

When you click on new post you will see the # symbol on the menu.

Click on this and paste the contents between the tags.

Submit and done.

it doesnt work. It stays stuck on searching for drives. im so pissed. Now im trying to reinstall ubuntu and it gets stuck too. Its like its not detecting the partition.  I have 1 harddrive split in two partitions one for windows and one for ubuntu. It seems like the ubuntu partition or something isnt working . I dont know! im frustrated

---

### Post by Rubi1200 on 2010-12-26
> **pinnacle65 said:**
> it doesnt work. It stays stuck on searching for drives. im so pissed. Now im trying to reinstall ubuntu and it gets stuck too. Its like its not detecting the partition.  I have 1 harddrive split in two partitions one for windows and one for ubuntu. It seems like the ubuntu partition or something isnt working . I dont know! im frustrated
Please try and stay calm!

I know it is frustrating, but we do not want you to potentially lose either Ubuntu or Windows.

If you are on the LiveCD, go to the terminal as before and post the output of this command:
```
sudo parted -l
```

---

### Post by pinnacle65 on 2010-12-26
> **Rubi1200 said:**
> Please try and stay calm!

I know it is frustrating, but we do not want you to potentially lose either Ubuntu or Windows.

If you are on the LiveCD, go to the terminal as before and post the output of this command:
```
sudo parted -l
```


screw it. I tried reinstalling and it couldnt even detect the linux partition , so i had to delete the linux partition thru windows, and I reinstalled Ubuntu.  Mods close this thread

---

### Post by susema on 2010-12-26
Try this please with LiveCD.

```
sudo fsck /dev/sdaX
```

X = Your Ubuntu root partition number..

---


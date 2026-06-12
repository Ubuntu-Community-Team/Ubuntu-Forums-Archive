---
title: "upgrade from 12.04 to 14.04 server edition"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by aor2 on 2014-11-25
I have upgrade 12.04 to 14.04 but when i booted it up something wrong with the grub...

[IMG]http://s30.postimg.org/frdj7emw1/DSC_1368.jpg[/IMG]

PLEASE HELP ME FIX THIS..thanks

---

### Post by carl4926 on 2014-11-25
So does the system boot?

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> So does the system boot?


Yes, but it stop until that screen..

when i chose any of the option below nothings happen another error.....

---

### Post by QIII on 2014-11-25
What error do you get then?

We can't help much unless we know what behavior you are encountering.

---

### Post by carl4926 on 2014-11-25
Select the top one and press 'e' on the keyboard
That way you can see the actual boot instructions and can edit them

---

### Post by aor2 on 2014-11-25
> **QIII said:**
> What error do you get then?

We can't help much unless we know what behavior you are encountering.

Here s the result when chosing option shown above

[IMG]http://s29.postimg.org/fw81wb8xz/DSC_1369.jpg[/IMG]

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> Select the top one and press 'e' on the keyboard
That way you can see the actual boot instructions and can edit them

Thanks for the reply i chose the top  one ang this is the result 
[IMG]http://s24.postimg.org/fvz1wurut/DSC_1370.jpg[/IMG]

ang then i select ang tried all the three i press b to boot but the output is this..

[IMG]http://s29.postimg.org/ji5lk7yfb/DSC_1371.jpg[/IMG]



ang then nothings happen the machine stops here...


Thanks...

---

### Post by carl4926 on 2014-11-25
Do you have a copy of the 14.04 media on DVD?
Or can you get that?

Was 12.04 an upgrade originally? I mean like from an earlier version? Like one that used Legacy grub?

---

### Post by carl4926 on 2014-11-25
> **aor2 said:**
> Thanks for the reply i chose the top  one ang this is the result 
[IMG]http://s24.postimg.org/fvz1wurut/DSC_1370.jpg[/IMG]

ang then i select ang tried all the three i press b to boot but the output is this..

[IMG]http://s29.postimg.org/ji5lk7yfb/DSC_1371.jpg[/IMG]



ang then nothings happen the machine stops here...


Thanks...

We can't read / see those

---

### Post by carl4926 on 2014-11-25
Struggling to read but if it's hd0,0

You could edit to

```
root (hd0,0)
    kernel /vmlinuz root=/dev/sda1 ro quiet splash
    initrd /initrd.img




```

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> Do you have a copy of the 14.04 media on DVD?
Or can you get that?

Was 12.04 an upgrade originally? I mean like from an earlier version? Like one that used Legacy grub?


I dont have anymore the 12.04 installer, but i have 14.04 amd64 server installer....


Thanks..

---

### Post by carl4926 on 2014-11-25
Try the edit I gave you
It means backspacing everything out
It only applies to the one time, if it works we would have to edit the file permanently

Another option might be to use the 14.04 media to chroot your system

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> Struggling to read but if it's hd0,0

You could edit to

```
root (hd0,0)
    kernel /vmlinuz root=/dev/sda1 ro quiet splash
    initrd /initrd.img




```


Here are some clear images

[IMG]http://s28.postimg.org/bf4111blp/DSC_1374.jpg[/IMG]

i choose root (hd0,0) ang press 'e' result is 


[IMG]http://s29.postimg.org/pw4shpfyf/DSC_1375.jpg[/IMG]

so how i am going to edit, how i can use the code you gave?sorry for my ignorance ..


Thanks..

---

### Post by carl4926 on 2014-11-25
Just type it in
Line by line

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> Just type it in
Line by line

Thanks..

So is this shopuld be the output?
[IMG]http://s8.postimg.org/rf7ru8p2t/DSC_1376.jpg[/IMG]

and then how to run using those sequence?if i press escape ang back again the cahnges i made will not be save..

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> Just type it in
Line by line


when i booted here is output

booting coomand-list

root (hd0,0)
 filesystem type is extfs, partition type 0x83
kernel /vmkinuz root=/dev/sda1 ro quiet splash

Error 15: Fiel not found

Press any key to continue....

---

### Post by carl4926 on 2014-11-25
Looks like you made a typo
[COLOR=#000000]vmkinuz
Is not correct

Look again and be careful to type exactly[/COLOR]

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> Looks like you made a typo
[COLOR=#000000]vmkinuz
Is not correct

Look again and be careful to type exactly[/COLOR]



yes i made i typho but in the screenshoot in the image i think it was correct,see the image i captured..'


Thanks,

---

### Post by carl4926 on 2014-11-25
Boot your live media and get the result of 

```
sudo fdisk -l
```
That's a lower case L not a number 1

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> Boot your live media and get the result of 

```
sudo fdisk -l
```
That's a lower case L not a number 1
here is the result

device boot                    start              end          blocks              id                    system

/dev/sda1 *                      numbers     numbers    numbres        83                linux
/dev/sda2                         numbers     numbers    numbers         82               linux swap / solaris
/dev/sda3                       numbers       numbers      numbres      83                 linux

---

### Post by aor2 on 2014-11-25
> **carl4926 said:**
> Boot your live media and get the result of 

```
sudo fdisk -l
```
That's a lower case L not a number 1


Hi Carl i resolve the issue using live cd thanks for the support.....


many many thanks.....):P

---

### Post by carl4926 on 2014-11-25
> **aor2 said:**
> Hi Carl i resolve the issue using live cd thanks for the support.....


many many thanks.....):P

OK
Well done

---

### Post by aor2 on 2014-11-26
> **carl4926 said:**
> OK
Well done


Thanks very very much.......;)

---


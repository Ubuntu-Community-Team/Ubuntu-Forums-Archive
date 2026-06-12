---
title: "Network printing on Ubuntu ONLY network"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-08-27
I was reading elsewhere on this forum that it was advised that if I wanted to setup a printer that is connected to the lpt1 port of one Ubuntu workstation (this printer does **NOT** have a print server card) on a Ubuntu **ONLY** network and then be able to print to that same printer from other Ubuntu workstations on the network, that I needed to use the GUI facilities for printer setup that is built into Ubuntu administration menus as opposed to using the CUPS printer administration.

Is there a printer expert that can advise me if this is true ?  The reason I ask is because after following every bit of advise that I could find on this forum I have still not been able to get this to work using CUPS facilities.

Is this something that is doable at this point in time or am I just trying to beat a dead horse because Ubuntu has not fixed this to the point that it will work ?

Thanks.

---

### Post by tagra123 on 2006-08-27
> **wpshooter said:**
> I was reading elsewhere on this forum that it was advised that if I wanted to setup a printer that is connected to the lpt1 port of one Ubuntu workstation (this printer does **NOT** have a print server card) on a Ubuntu **ONLY** network and then be able to print to that same printer from other Ubuntu workstations on the network, that I needed to use the GUI facilities for printer setup that is built into Ubuntu administration menus as opposed to using the CUPS printer administration.

Is there a printer expert that can advise me if this is true ?  The reason I ask is because after following every bit of advise that I could find on this forum I have still not been able to get this to work using CUPS facilities.

Is this something that is doable at this point in time or am I just trying to beat a dead horse because Ubuntu has not fixed this to the point that it will work ?

Thanks.


I'm not a printer expert but you may try my method of working around the broken cups.

Here's a workaround until it gets fixed:

[http://ubuntuforums.org/showthread.php?p=1428724#post1428724](http://ubuntuforums.org/showthread.php?p=1428724#post1428724)

---

### Post by wpshooter on 2006-08-27
Do you think this will be fixed in Edgy ?

I can believe I would have to do all of this just to network/share a printer !!!

Thanks.

---

### Post by tagra123 on 2006-08-27
> **wpshooter said:**
> Do you think this will be fixed in Edgy ?

I can believe I would have to do all of this just to network/share a printer !!!

Thanks.



I sure hope it gets fixed.

In my opinion, this kind of problem is unacceptable and had to be known about before it was released. It makes you wonder if anyone tests the printing before releasing the software. 

Every once in a while I read post where someone says  "Who prints anyway" -- The truth is I don't know anyone  who doesn't need to use a printer.

There are only actually a couple of extra steps to do it this way --> setting up samba. If you are already sharing files there's not that much to do that's extra. -- (I think if samba is already installed and working you would only have to delete the two comments in front of the printer lines.

---

### Post by wpshooter on 2006-08-27
Delete comments from where ???

When you setup SAMBA, is there a place in SAMBA setup or elsewhere that you designate that you want to share a printer ?   

Is SAMBA just for file sharing or does it allow you to share **DEVICES** also ?  I have asked this question a number of different time and in different ways and I have never gotten an answer.

Thanks.

---

### Post by tagra123 on 2006-08-27
Yes you can share printers through samba -- as far as the other computers know its a printer on a windows machine

The two lines I was referring to are in the smb.conf

Edit the smb.conf file


```
gedit /etc/samba/smb.conf
```



Uncomment these two lines (about mid way through he smb.conf file:

It will look like this:
```
#printing = cups
#printcap name = cups
```


Make it look like this

```
printing = cups
printcap name = cups
```

Save the file and exit the text editor.

Read through the rest of this and the link above if you are having trouble.

It should only take 5 to 10 minutes following the directions in the how to.



Next make sure that the Domain Name of all computers that are going to be using this printer are set to the same name. Since the Windows Virtual Machine was already set for the MSHOME network thats what I used too. No flames please. Any name will work here as long as all are in the same domain name

To check or change the domain from the Panel Menu Select: System > Administration > Networking

Click on the "General" Tab

Make Sure Domain name : is set to MSHOME (Unless you chose another name)


Restarting cupsys should make everything accessible, if not reboot the computer.

Try


```

sudo /etc/init.d/cupsys restart
```

or Reboot.

---

### Post by wpshooter on 2006-08-28
> **tagra123 said:**
> Yes you can share printers through samba -- as far as the other computers know its a printer on a windows machine

I do NOT have any **windows** machines.  Machine that printer is connected to is a Ubuntu machine and ALL other machines are also Ubuntu.  Will this still work ???

Thanks.

Please ignore I mis-read the first line.  It says as far as the other computers know.

---

### Post by Mesa on 2006-08-28
Looks like that I am not alone with problem in the new CUPS regarding network printing.

---

### Post by wpshooter on 2006-08-28
Is your problem similar to mine ?

Have you had any success to speak of ?

Thanks.

---

### Post by tarclee on 2006-08-28
i am facing same problem,all my pc is using ubuntu,the printer connect to usb port of my pc.network user can't print my printer.any1 can help?

---


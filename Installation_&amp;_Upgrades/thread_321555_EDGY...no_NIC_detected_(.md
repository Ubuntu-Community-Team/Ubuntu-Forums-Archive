---
title: "EDGY...no NIC detected :("
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by niwhsa on 2006-12-19
hi guys, yesterday i installed UBUNTU EDGY on my system ...

during installation,a message came up saying that no network interfaces were detected
{but i have an ethernet card plugged into my pci slot }
it gave me 2 options..1 to go back and try again and the other to continue.. i tried the former a few times but to no avail..so i continued the installation..

after installation, i tried to download a [driver]("http://www.techcomindia.com/download_driver.asp") for my ethernet card from the [manufacturers website]("http://www.techcomindia.com")
and it asked me to compile the c code given..
i tried to compile using the regular
cc filename.c  and 
cc filename.c -ll  and also 
make install 

{ i tried the make install  a  lot later }
none of them worked...it gave a lot of errors {atleast 50}

also my modem is a winmodem with support for using USB and ethernet .. but UBUNTU detects my modem as a USB device but i cannot connect it to interent...i feel i need a driver for that ..

so ppl please help me connect to the internet using UBUNTU....

TIA

---

### Post by niwhsa on 2006-12-20
](*,) ](*,) ](*,) 

guys i need some help...:evil: :evil: :evil: :evil: :evil:

---

### Post by Wall86 on 2006-12-20
can you download the ubuntu 6.10 i386 version (regular download) and oot to livcd, then run "sudo lshw"? that should tell ya if it is there and there is no drivers, or if it is not detecting it at all

What kind of card is it?

---

### Post by niwhsa on 2006-12-20
@ ^^  

[this]("http://www.techcomindia.com/itemdetail.asp?Cat=PCI%2FI%2FO+CARDS&CatID=96&prodid=503&ProdName=Lan+Card+32+bit+PCi+10%2F100bps") is my  card and  i have uploaded the driver folder [here]("http://rapidshare.com/files/7970852/techcom_lan.rar.html")...

and after searching on the net , i have come across[ this]("http://www.geocities.com/rohitksethi/") page which fortunately tells me abt the installation using the same card that i have...
but now my system got messed up .. {i tried to do some things which in hindsight i shud not have done ;-) }

so i have now completely reinstalled UBUNTU EDGY...

after the complete reinstall,i have done only these ..

1> installed the ndiswrapper using the command

```

sudo apt-get install ndiswrapper-utils
```


2> after installing it, i typed in the command
```

ndiswrapper -i netslnt.inf

```
as mentioned in the link

3> now this
```

ndiswrapper -l

```
which displayed
```

Installed ndis drivers: netslnt driver present

```

4> then i typed in the command
```


modprobe ndiswrapper

```
which gave me this error
```


FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

now what shud i do???

---


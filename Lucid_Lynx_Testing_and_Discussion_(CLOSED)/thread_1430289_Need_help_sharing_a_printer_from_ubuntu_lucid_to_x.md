---
title: "Need help sharing a printer from ubuntu lucid to xp"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-15
i have a printer connected to my ubuntu computer when i try to print from xp to seven everything is fine meaing everything is fine on xp when i try to print to ubunt i get this messeges from xp i'm translating so it might not be accurate "can't show properties, background print spooler not running"on xp he's running on ubuntu i'v used gadmin-samba to set it to work and the other messege i get is "rpc server not avilable" which i don't know how to fix.

how can i fix this problems?

thanks in advance.

---

### Post by aviramof on 2010-03-16
no one knows why i get a problem with rpc?

---

### Post by c0nfusedami on 2010-03-16
This was the information that I used given to me by user johnson.d to get my printing set up and it worked flawlessly with xp however I haven't been able to get 7 to connect to it out of laziness mainly. This configuration uses samba and i believe cups to set everything up which should be installed on your system already. If not install then and carry on with configuration. I think it may also be necessary to use a static I.P. address also. Let me know if you need info on that. 

1) Configuration on Ubuntu side:

Edit the /etc/samba/smb.conf file and see if these lines are uncommented,add these lines if not present

[ printers]

comment = All Printers
path = /var/spool/samba
browseable = no
printable = yes

2) Configuration on windows client:

i) Start menu-> Printers and faxes -> Add a printer
ii) A window will open click next
iii) Select "A network printer, or a printer attached to another computer" and click next
iv) Select "Connect to this printer (or to browse for a printer, select this option and click next)"
Enter \\< ip-address >\<printer name as in ubuntu> and click next
v) It will connect to the printer and may say that the driver is not installed (if driver is present in Windows xp it will proceed without driver installation)
vi) Install the drivers
vii) It will prompt "Do you want to this printer as the default printer?". Select your choice an click next
viii) Click finish.

---

### Post by aviramof on 2010-03-16
thanks for the help but i already gave up ubuntu i have come to the conclustion that ubuntu is TERRIBLE!!! in networking and in some other things like hardware drivers all i have managed to do is to connect to my xp machine with rdp and share internet to xp with firestarter and i can acess xp from ubuntu but i can't do the opposite except via the rdp local drive option and i have no idea why and because of it can't also share my printer in the end and i'v wasted enaf time on this problem i guess i would need to do all my printing from the xp via windows seven in the end and probbly a few other things..

---

### Post by c0nfusedami on 2010-03-17
Too bad ubuntu can be really fun if you have the time and patience. Everything you want and need to do is possible you just have to work at it.

---

### Post by samh785 on 2010-03-17
> **c0nfusedami said:**
> Too bad ubuntu can be really fun if you have the time and patience. Everything you want and need to do is possible you just have to work at it.
Good things come with time. +1

---

### Post by aviramof on 2010-03-17
i tried everything i could possibly think off but samba got me no where i can't even get windows xp to recognize ubutnu at all let alone enter it and share a printer.
 
and it's not so fun except compiz i found nothing very intresting in this os no good hardware recognition no good display option no good networking i spent four days just to try to share a printer between xp and ubuntu with no luck i can't even get xp to recognize ubuntu at all
and basicly there are so much problems with this os it's incredible you can work with at all for examle today i installed xubuntu and discoverd
that there is no rdp software there so i can't connect to my second computer and i also can't use gnome-rdp so what should i do now?
 
naturaly removed xubuntu and install ubuntu again but i gave up on ubuntu so i'v removed xubuntu and i'm not going to install again or ubuntu in the next few months.

---

### Post by cariboo on 2010-03-17
I would suggest you try Karmic (9.10). 

It is recommended that if you want to run a testing version, you should have quite a bit of previous experience fixing problems that will and do crop up during the testing cycle. Another thing is not to run a testing version as your main computer system, run it on a separate partition, so that you can fall back to a previous version when things break.

---

### Post by aviramof on 2010-03-18
9.04 and 9.10 don't want to connect to my isp via pppoeconf i already tried them and i'm not installing 8.10 it's too old for me.
 
and by the way anyone can tell me why xubuntu don't have and rdp software i mean one of the biggest problem ubuntu in all version is lack of competabily each version has it's own version of a software and if you download something like xubuntu lubuntu kubuntu you might find out that
a spesifice software don't exist there and that is maybe the biggest problem i think linux ubuntu have.
 
xubuntu for instance is looking great he works similer to gnome but have some more options on desktop and a slightly better desing in applications and places and yet he has virtually no networking tools at all and that is he's big problem.

---


---
title: "U320 HostRAID Driver (Hardware)"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by Syirrus on 2006-12-01
I just purchase a server [http://www.newegg.com/Product/Product.asp?Item=N82E16816101059]("http://www.newegg.com/Product/Product.asp?Item=N82E16816101059")
which an Adaptec AIC-7902 Dual-Channel Ultra320 SCSI which supports RAID 0, 1, 10.  I have 4 scsi HDD and setup the array to do RAID 10.  When I try to install linux (Ubuntu (my perference) Redhat, or Centos)) it fails to find my newly created array.  It will show all four drives, but not the array that I created (single 74gb instead of x4 36gb drives).  I tried installing RAID drivers for Redhat with no success.  How can I enable Hardware RAID in linux?  Is it already enabled?  Should I do a LVM? 

Syirrus

---

### Post by karaluh on 2006-12-04
> **Syirrus said:**
> I just purchase a server [http://www.newegg.com/Product/Product.asp?Item=N82E16816101059]("http://www.newegg.com/Product/Product.asp?Item=N82E16816101059")
which an Adaptec AIC-7902 Dual-Channel Ultra320 SCSI which supports RAID 0, 1, 10.
Syirrus

Adaptec's HostRAID isn't hardware raid. Disable HostRAID and configure software raid.

---

### Post by Syirrus on 2006-12-06
are you serious??  It had built in raid I thought.  In fact you can set the array up via adaptecs utility

---

### Post by karaluh on 2006-12-07
> **Syirrus said:**
> are you serious??  It had built in raid I thought.  In fact you can set the array up via adaptecs utility

Unfortunately, I am serious. 
[http://adaptec-tic.adaptec.com/cgi-bin/adaptec_tic.cfg/php/enduser/std_adp.php?p_faqid=13298&p_created=1113920469&p_sid=PZxORvoi&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTUxJnBfcHJvZHM9MCZwX2NhdHM9MCZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9aG9zdHJhaWQ*&p_li=&p_topview=1](http://adaptec-tic.adaptec.com/cgi-bin/adaptec_tic.cfg/php/enduser/std_adp.php?p_faqid=13298&p_created=1113920469&p_sid=PZxORvoi&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTUxJnBfcHJvZHM9MCZwX2NhdHM9MCZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9aG9zdHJhaWQ*&p_li=&p_topview=1)

Quoting official Adaptec www:
"HostRAID is an integrated RAID technology that adds entry level RAID support. It is also called intelligent RAID on chip (iROC) or **software RAID** and it is build into the firmware of the controller. **There is no additional RAID processor on HostRAID cards. **"

---

### Post by Syirrus on 2006-12-07
Shazbot oh well and thank you.  I have another question... I'm looking to run an enterprise level web site and I was wondering is ubuntu right for the job, or should I use redhat or centos?  I'm much more comfortable with ubuntu btw :)

Syirrus

---

### Post by karaluh on 2006-12-07
> **Syirrus said:**
> I'm much more comfortable with ubuntu btw :)
So stay with it. It'll do it's job well.

---


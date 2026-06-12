---
title: "[SOLVED] tar issue"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by gishaust on 2007-08-01
hi everyone 

I have something that is really puzzling to me. I have tar other files on this computer and it has not been an issue until now.

I have downloaded ddclient (several versions) to an xpbox and then I transfer the file to my server then I try unpacking it and it won't

this is what I have done,

the file ddclient.1.2.5.orig.tar.gz

sudo tar -zxvf ddclient.1.2.5.orig.tar.gz (did not like that at all)
tar -zxvf ddclient.1.2.5.orig.tar.gz (did not like that at all)

gunzip  ddclient.1.2.5.orig.tar.gz (it liked that and worked well)
Then I 
 tar -zxvf ddclient.1.2.5.orig.tar (it says the file is not there)
 tar -xvf ddclient.1.2.5.orig.tar (it says the file is not there)

at all times I am in the folder where the file is place

can anyone help me

gishaust

---

### Post by girishv on 2007-08-02
the z flag is to unzip the file. You can not use this flag on a file which is already unzipped.
Try using
tar -xvf filename.tar

Are you sure you are not making any typos while entering the command. One more time, make sure the file is there by running ls and try to use tab to complete the filename like
tar -xvf ddclient<tab>

Girish

---

### Post by aysiu on 2007-08-02
Instead of typing "did not like that," can you retype the actual error messages? What error message do you get, for example with this command? ```
tar -xvzf ddclient.1.2.5.orig.tar.gz
```

---

### Post by gishaust on 2007-08-02
thanks for the replys

when I say that the 'machine does not really like that'. What I should of said sorry is that the machine does nothing at all it just freezes up no command line nothing I have to restart the computer.

i ls and the file was there then I ddclient<tab> (very cool) it brought up the rest of the file

I tried tar -xvf  ddclient.1.2.5.orig.tar it said it there was no such file and  was skipping to the next header. 

If you need any other information just point and I will run and get it.

gishaust

---

### Post by gishaust on 2007-08-02
I have fixed it!!!!!!!!!!!!

this is what I did,

I went to the dyndns web site and download the file from there.Then placed it on the server I also apt-get install tar it said that it was the latest version of tar. then I sudo tar -zxvf ddclient.tar.gz and it work first go. don't ask me why, I am only beginner. But there is great satisfaction in fixing it Yeh, Yeh, Yeh.

Gishaust

---


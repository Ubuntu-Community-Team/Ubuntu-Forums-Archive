---
title: "Installing programs without internet"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by oniko0 on 2005-05-04
Hello everyone!

Being unable to access the internet through my USB modem, I decided to download tar.gz files using Windows, and transferring the files to Linux for setup. However, once I obtained the files, I have no clue how to install the programs from tar.gz files.

Could anyone help, please?

Thank you.

Oniko

---

### Post by dave9191 on 2005-05-04
That depends what you are trying to install. 

.tar means its an archieve file and .gz that its compressed using gzip. Im guessing that you have source code in there, but it could be anything. You need to unpack the archieve and follow the readme or instruction. If it is source code you will need to compile it using the commands

make
sudo make install

That will work assuming that no errors have occured. And you will need lots of libaries to compile stuff on your system. So that will mean you will have to get the required ones first. 

If its a .deb file in there, then its a lot easier to install. You use the dpkg command

dpkg -i packagename.deb

If its an rpm, then there is a convertion program, but thats slipped my mind atm. 

Dave

---

### Post by oniko0 on 2005-05-04
Hello again, Dave!

The package I have in mind is OOo 1.9 beta. I downloaded it to my computer, but I'm not sure where to proceed from there.

The file contains RPM-format files, quite a number of them too.

Any suggestions?

Thank you.

---

### Post by dave9191 on 2005-05-04
My suggestion is to try and find a debian based package if possible (.deb) since you are running a debian based system. 

And if thats not possible, unpack all the files into a directory and check for a README. if there isnt one there then I would do 

alien *

that should convert all the rpms into deb files (this is still experimental, so it might not work). Assuming you didnt get any errors then 

dpkg -i *.deb

that will install all the newly created deb files. That last command will probably need sudo b4 it.

---

### Post by oniko0 on 2005-05-04
This didn't quite work.

GOOD NEWS: Successfully converted file to .deb
BAD NEWS: Did not get much result.

Here's what I did: I converted the tar.gz file (maybe I'm not supposed to do that...) into .deb, becoming "/home/zzp/ooo2beta_1-2_all.deb"

In terminal , I typed: "sudo dpkg -i /home/zzp/ooo2beta_1-2_all.deb"  which displayed (as is):

    (reading database ... 55013 files and directories currently installed)
    Preparing to replaced ooo2beta_1-2 (using /home/zzp/ooo2beta_1-2_all.deb)
    Unpacking replacement ooo2beta ...
    Setting up ooo2beta (1-2) ...

And that's the end of it. If the file installed, I did not see it.

Thanks for the help. Anything else I could try? Or any folder I should look in to find the program?

---

### Post by dave9191 on 2005-05-05
I would have thought that if you tried to convert the .tar.gz it would reject it. You were supposed to unpack that file first and then convert the rpm's you said were inside. 

and if you install something and need to fine it, then do 

sudo update db
locate what_you_want_to_find

That will update the file db for searching and locat things for you :)

---


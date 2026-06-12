---
title: "[SOLVED] Error 256 when installing to USB drive"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by walter_j on 2008-11-02
When installing to a kingston 8 GB USB drive using the "create a USB startup disk" in ubuntu 8.10, I get a fail message "error 256" in the usb log file. What does the message mean, and can I resolve this problem?

8.10 looks good so far. Even nvidia driver is working ok so far.

walter

---

### Post by adderd on 2008-11-03
I have the same problem in trying to use a 2GB sandisk USB drive. I've tried reformatting several times to no avail. I'd really like to know why this error is happening.

---

### Post by snadrus on 2008-11-12
I tried making an 8gb disk off the i386 live CD as well & saw this. 

After seeing the traceback of: /usr/share/usb-creator/install.py -s /media/cdrom0 -t /media/disk -p 1063
blah  Traceback (most recent call last):
blah   File "/usr/share/usb-creator/install.py", line 147, in <module>
blah     main(source, target, persist)
blah   File "/usr/share/usb-creator/install.py", line 73, in main
LOOK!     shutil.copyfileobj(sourcefh, targetfh)
blah   File "/usr/lib/python2.5/shutil.py", line 26, in copyfileobj
blah     buf = fsrc.read(length)
LOOK! IOError: [Errno 5] Input/output error

..I modified that python script to add right under the line:
old                    shutil.copyfileobj(sourcefh, targetfh)
new		except:
new		    sys.stdout.write(sourcepath+"\t"+targetpath+"\n")
new 		    sys.stdout.flush()	
Don't copy the old/new stuff, that just makes it readable.

To save, I did: sudo chmod 777 /usr/share/usb-creator/install.py

Running again gave 2 "problem areas":
   /media/cdrom0/umenu.exe  /media/disk/umenu.exe
   /media/cdrom0/wubi.exe   /media/disk/wubi.exe
I don't care, they're windows files & shouldn't apply here. 

It finished successfully. Wanted to try it out via virt-manager, but it can't boot off USB, oops. Restarting to test.

---

### Post by snadrus on 2008-11-12
The USB disk worked exactly as expected. 
Quick Guide:
 Terminal: "sudo nautilus" 
 Copy the attached py file to overwrite /usr/share/usb-creator/install.py

This should also be submitted as a bug report.

---

### Post by walter_j on 2008-11-22
The last update fixed this problem.

Walter

---

### Post by jeremy1080 on 2008-11-30
Thanks it really helped me. Why does it not work any ways?

---


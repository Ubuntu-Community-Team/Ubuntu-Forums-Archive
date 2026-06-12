---
title: "systemcrash while installing textlive-fonts-extra"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by cmpcmp on 2010-01-02
I was multitab browsing (around 15 tabs) in latest firefox for karmic koala (9.10) 
and at the same time downloading (probably already auto-installing) in synaptic-package-manager the package: textlive-fonts-extra (and other necessary packages; this was around 90 mb download and 250 mb installation)

suddenly the pointer doesn't move anymore, (Alt+tab , and other combinations also didn't work anymore)
and I hold the power button untill the computer is turned off,
when I reboot I get this message
"invalid system disk, replace it and press any key to continue"

now I'm using a livedisc to boot the computer (jaunty 9.04)


To rebuild the system i think to manually install the packages that probably were interupted while installing and made it not work anymore

The packages to be installed when text-live-fonts is marked for install (in synaptic opened from the livedisc) are:
dvipdfmx
lmodern
text-common
texlive-base
texlive-base-bin
texlive-base-bin-doc
texlive-common
texlive-doc-base
texlive-fonts-extra-doc

This may be different with 9.10 configuration (can anybody look to see which are necessary with 9.10)


Does anybody have a good idea for this problem?

I think the computer wasn't responding anymore because I used too many tabs at ones.
I had this same problem a few times before in the past weeks but then I wasn't installing something and the computer did restart and firefox restored all the tabs.




I cannot enter  /home/  from the livedisc (no permission)
and it's necessary , I am in the middle of exams and i need to print the paper that is on the disc by monday

Is there a way to enter it via command console?


PS is this the place where i can post such problems?


can somebody help?

---

### Post by procras on 2010-01-02
You should be able to see what is on your harddrive from the live cd.

Make yourserf a superuser
$ sudo -s

Create a mount point
$ mkdir /media/myolddisk

Mount the partition
$ mount /dev/sda1 /media/myolddisk
/dev/sda1 means the 1st partition of the first disk sda
Your partition is probably different.
You can look at the partitions with gparted

Look at your files
$ ls /media/myolddisk/home/username/files

Back them up somewhere safe ie on network, CDR or on flash usbdrive

---

### Post by cmpcmp on 2010-01-03
I have installed the texlive-fonts-extra package and the other packages to the harddrive and the computer boots,

then I had to change 2 permissions,

1 because I couldn't use sudo
'chmod 0440 /etc/sudoers'

2 because I couldn't log in and got this error

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=nl_BE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied

I found two options 'chmod a+w /tmp'  and  'chmod 1777 /tmp'
but I do not know the difference, I used the first one.

9.10 works but seems as a new 9.10 install.



Still a problem:

computer@computer:~$ cd /
computer@computer:/$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [  ] into the user session keyring
mount: Operation not permitted


Does someone know the answer

---


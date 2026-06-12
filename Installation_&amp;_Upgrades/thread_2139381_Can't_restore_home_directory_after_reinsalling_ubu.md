---
title: "Can't restore home directory after reinsalling ubuntu 12.04"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by J Harp on 2013-04-26
Using sbackup, I backed up just before reinstalling. After reinstall I set up deja-dup, and Ubuntu One. Now when I try to restore the home directory by doing deja-dup --restore, and copy and paste the backup file, I always get an error of some kind. 

The same thing happens if I try duplicity --restore. Each new attempt seems to return a different error. Trying to restore with deja-dup now sometimes brings up a gui asking "restore from where" with several options, at first MyBook was listed, that's where the backups are stored, I chose it, and got an error, can't recall what. On the last two or three attempts, MyBook wasn't among the options, choosing deja-dup brings up various errors.

I have spent hours searching for how to do this, so far nothing has worked. Can someone help? Thanks.

Jim

---

### Post by darkod on 2013-04-26
I'm not familiar with sbackup, what is that? Usually you would restore with the same program, are you trying to restore with a different one?

Why don't you simply copy the files, you don't even need a special backup program. In that case the restore is very easy, you simply copy back.

Whether network disks show up or not sounds like network connectivity issues. Maybe that's where your problem is.

Also, if possible try noting down the error messages, and then googling them. Sorry, but "can't recall" is not an option. Unless the message goes away really really fast, note it down.

---

### Post by J Harp on 2013-04-26
sbackup (simple backup) was a forerunner to deja-dup, they both use duplicity. I've tried restoring from MyBook, with duplicity, and with deja-dup. I have been googling everything, but so far nothing has given me an answer which would work. many of the error msgs. would take me 15 minutes to scribble down, and I have not found a way to copy them from a terminal. If someone would tell me how to do that, it would help.

I'll try your suggestion of copying the files, thanks for that. I'll have to google that too, as I don't know how to do it.

---

### Post by darkod on 2013-04-26
I don't know how sbackup makes the backup file. Is it like a single file, a compressed archive, or the complete folder structure like a simple copy would do it.

In any case, if copying manually by cp don't forget to pass options to keep the file ownership and permissions the same during copying back. With cp the command would be:
```
sudo cp -ax /source /destination
```

The -ax option for cp are all you need to keep ownership and permissions. I have copied my whole home folder when moving from hdd to ssd half a year ago, worked perfectly. Not even one problem with ownership or permissions. It keeps them untouched.

In terminal if you move the mouse pointer on the top bar to show the window menu, there should be like Edit menu where you can find like Mark, or Copy, which should help you copy text to paste it later. Or simply make a screenshot with the terminal window open, and later you can study the jpg screenshot as long as you want. In ubuntu there is an application literary called Screenshot.

---

### Post by J Harp on 2013-04-26
Thank you Darkod;

The sbckup is a sigtar.gpg. I tried opening an older one and got the following.

Could not display "/media/MyBook/sbackup/dupli...o201300417T012126Z.sigtar.pgp"      Next line of msg. There is no application installed for PGP/MIME-encripted message header files. Do you want to search for an application to open this file?      I'll look into this later, it's bedtime now.

I want to study the Ubuntu Documentation before going much deeper into this, I have forgotten much of what little I ever knew about working with the command line. I do appreciate your trying to help, and I'll report on my success or failure. I have a plumbing job to do before I can get back to it, so I'll work on it when I can.

Jim

---

### Post by J Harp on 2013-05-01
Still no restore. I installed KGpg, and made the key pair and tried to decrypt the file, tried several times, always getting the error, (As a GUI window) "decryption failed". One time the message had a second line, "You probably do not have the decryption key".

After much searching and trying every suggestion I could find, I have got to this, (copied from a screenshot).

jim@jim-HP-dc5000-uT-PB470A:~$ sudo mkdir from pkg core utils /file:///media/My%20Book/sbackup/duplicity-new-signatures.20130423T132746Z.to.20130424T145625Z.sigtar.gpg 
[sudo] password for jim: 
mkdir: cannot create directory `/file:///media/My%20Book/sbackup/duplicity-new-signatures.20130423T132746Z.to.20130424T145625Z.sigtar.gpg': No such file or directory
jim@jim-HP-dc5000-uT-PB470A:~$ sudo mkdir -p file:///media/My%20Book/sbackup/duplicity-new-signatures.20130423T132746Z.to.20130424T145625Z.sigtar.gpg 
[sudo] password for jim: 
jim@jim-HP-dc5000-uT-PB470A:~$ gpg --output clear.txt --decrypt/file:///media/My%20Book/sbackup/duplicity-new-signatures.20130423T132746Z.to.20130424T145625Z.sigtar.gpg /restores
gpg: Invalid option "--decrypt/file:///media/My%20Book/sbackup/duplicit"
jim@jim-HP-dc5000-uT-PB470A:~$ 

Googled Invalid option and got a list of available options which included   "--decrypt [file]". I don't know what to try next, if I've learned one thing from all this it''s NEVER to trust a backup system which is not 100% automatic when restoring files. If I had taken a picture of my home folder, I could have had what I want from it rebuilt by now.

---

### Post by darkod on 2013-05-01
As I said, I haven't used that software but from this latest info it seems that it encrypts the backup file, either because you selected to do that when making the backup, or it does it on its own.

Decrypting the file without the passphrase will be very difficult if not impossible. I don't think creating new keys can help, you need the original passphrase. Otherwise anyone who gets hold of your faile could decrypt it.

---

### Post by J Harp on 2013-05-01
I think it must have done it on it's own. As far as I can recall, I've never knowingly set up any encrypted backup scheme before. I have no passwords for sbackup, I write down a clue to every password I make before entering it in the computer.

MyBook is an external hard drive, These files have never been sent to any offsite backup as far as I know. If there is no way to recover the original passphrase, then I'll just wipe MyBook so it won't be bugging me. I can use it for storing pictures and such.

I have the bookmarks for the sites where I got most of the doc.s and pic.s I'm interested in, so I can slowly get them back. Thank you very much for your advice and help.

---


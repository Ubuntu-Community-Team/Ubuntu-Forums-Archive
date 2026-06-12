---
title: "vi editor  from remote doing something weird"
date: 2020-05-29
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2020-05-29
I upgraded to 20.04 on a couple of Dell laptops and both do the same thing. If I remotely login to one of these, could be with ssh or telnet and try to edit with vi, then the screen shows something that looks like graphic characters, not ascii. It does not happen if I do it locally on the machine.

---

### Post by Impavidus on 2020-05-30
I think that the terminal you use to set up the connection to your remote machine uses a different character encoding than what vim puts out. These days everything should be utf8, which is a superset of ascii.

---

### Post by TheFu on 2020-05-30
Definitely a terminal/character set issue. Check the options in your terminal.  Sometimes, vim needs a hint to use UTF8 in the first line, otherwise it will choose ASCII. Add
```
set encoding=utf-8
```
to your ~/.vimrc file, but the hint is still necessary, IME.

And please don't use telnet or plain FTP ... ever, anywhere. Neither should be enabled on any Unix since before 2002.

You can use vim **rsync://server/path-to-file** to remotely edit files. This assumes ssh and rsync are setup on both sides.

And please don't use the soon-to-be-deprecated rsa ssh-keys. Those have been the defaults far too long.  Time to replace those keys everywhere.

---

### Post by danielsender on 2020-05-30
I put that in .vimrc but the problem remains.

---

### Post by TheFu on 2020-05-30
Did you do the other things too?

---

### Post by danielsender on 2020-05-30
I tried with ssh. I couldn't figure out how to use vi with rsync.

---

### Post by danielsender on 2020-05-30
Interesting, when I typed:

vi rsync://daniel@bach//home/daniel/fernando

it didn't work, so I installed vim and now typing:

vim rsync://daniel@bach//home/daniel/fernando

it does.

But now when I enter vi <somefile> it appears that is using vim because of the different text colors.

Anyway, thanks for your help.

---

### Post by TheFu on 2020-05-31
There are many different versions of vim.  It is common for programs to see how they were invoked and behave specifically in that manner.

```
sudo apt search vim-
```
will show some other package ideas.

---


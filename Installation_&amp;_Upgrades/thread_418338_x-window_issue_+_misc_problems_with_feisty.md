---
title: "x-window issue + misc problems with feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by the_zoor on 2007-04-22
zoor@zoor-laptop-ubuntu:~$ epiphany 
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
open dsp: Enhet eller resurs upptagen
open dsp: Enhet eller resurs upptagen
The program 'epiphany' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 124 error_code 168 request_code 146 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
zoor@zoor-laptop-ubuntu:~$ 

This is the output my ubuntu-distro feisty after a while. I've been having alot of problems after the update. First of all the sound didn't work as good as I've hoped. I had to change a couple of settings in system to make it work at all. Had to re-install all the codecs for mp3/ogg playing, using amarok.

And now the x window system gives me a hard time. It crashes every now and then. Same with the keyboard and mouse. Its simply buggy as hell. Some time my keyboard refuses to respond. This occurs both on my laptop, where I'm writing this right now. And on my other computer with a ps/2 keyboard.


Seems like a lot of people has problem with this on the forum. Anyone seem to found the issue? Hope an update is on its way because this is driving me nuts ](*,)

Edgy didn't gave me this much problems in the beginning... :(

---


---
title: "Grub error 1?"
date: 2006-04-18
forum: Installation &amp; Upgrades
---

### Post by Patroni on 2006-04-18
Just installed 5.1 to a brand new blank hard drive, as far as I can tell all went well. No errors were reported. Installer asks me to remove CD and restart which I do only to be greeted with 

Grub loading stage1.5.

Grub loading please wait...

Error 1

And thats it! just hangs.

These error messages amaze me these days do programmers find it impossible to print what the error actually is instead of just error 1.

---

### Post by sxtz on 2006-04-18
[quote=Patroni]
Grub loading please wait...

Error 1

And thats it! just hangs.

These error messages amaze me these days do programmers find it impossible to print what the error actually is instead of just error 1.[/quote] 
There's reasons why they assign cryptic error codes instead of error messages. I'm sure such reasons would be better explained by the GRUB programmers than by myself, though.... :mrgreen:

A list of some GRUB Error Codes and Messages can be found here: [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html]("http://www.uruk.org/orig-grub/errors.html")

In relation to your predicament, the page says:

> 
**14.3 Errors reported by the Stage 2**

   The general way that the Stage 2 handles errors is to abort the operation in question, print an error string, then (if possible) either continue based on the fact that an error occurred or wait for the user to deal with the error.     
 The following is a comprehensive list of error messages for the Stage 2 (error numbers for the Stage 1.5 are listed before the colon in each description):       
  1 : Filename must be either an absolute filename or blocklistThis error is returned if a file name is requested which doesn't fit the syntax/rules listed in the [Filesystem]("http://www.gnu.org/software/grub/manual/html_node/Filesystem.html#Filesystem").
    

so maybe your /boot/menu.lst is borked..

is it an old machine?  the more information you post about your machine, the more likely someone will be able to help you.  

(by the way, the link found above was located by searching google for "grub error 1" and was the second link in the results)

---


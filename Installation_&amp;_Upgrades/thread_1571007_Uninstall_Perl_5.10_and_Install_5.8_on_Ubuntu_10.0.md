---
title: "Uninstall Perl 5.10 and Install 5.8 on Ubuntu 10.04"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by skumar1 on 2010-09-09
[SIZE=2][COLOR=Navy]Hi All,[/COLOR][/SIZE][COLOR=Navy]

[/COLOR]     [SIZE=2][COLOR=Navy]I was using Ubuntu 8.04 with  installed Perl 5.8.8. I had installed  Bugzilla 3.4.4 with some custom scripts and it was working fine. I had to  upgrade Ubuntu from 8.04 to 10.04 and automatically Perl is also upgraded from  Perl 5.8 to 5.10. Now accessing Bugzilla displays error message related to Perl  module. While trying to run checksetup.pl, I am  getting following error message :
root@cvsnew:/var/www/bugzilla-3.4# perl  checksetup.pl
*
This is Bugzilla 3.4.3 on perl 5.10.1
* Running on  Linux
2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26  UTC
2010
Checking perl modules...
Checking for CGI.pm (v3.33)  ok:
found v3.48
[B]perl: symbol lookup  error:
lib/i486-linux-gnu-thread-multi/auto/Digest/SHA/SHA.so:  undefined
symbol: Perl_Tstack_sp_ptr[/B]

Accessing Bugzilla throws  :
**"500 Internal Server Error"**.[/COLOR][/SIZE][COLOR=Navy]

[/COLOR]     [SIZE=2][COLOR=Navy]I explored this issue and found that this issue has come up  because upgrading Ubuntu upgrades Perl 5.8  to 5.10 automatically. It seems like Perl 5.10.1  isn't binary compatible with the previous.[/COLOR][/SIZE][COLOR=Navy]

[/COLOR]     [SIZE=2][COLOR=Navy]Now, I want to uninstall Perl  5.10.1 and Install Perl 5.8.8 on my Ubuntu 10.04 box. I will appreciate if  someone has already done that or share the required steps/commands to do it. Thanks for your quick  response.[/COLOR][/SIZE][COLOR=Navy]

[/COLOR]     [COLOR=Navy][SIZE=2]Regards
Kumaar[/SIZE][/COLOR]

---


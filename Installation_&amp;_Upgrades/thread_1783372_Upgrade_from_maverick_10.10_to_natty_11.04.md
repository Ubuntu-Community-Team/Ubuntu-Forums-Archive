---
title: "Upgrade from maverick 10.10 to natty 11.04"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by wood9h on 2011-06-15
I just tried to upgrade, but seems that packages has changed from 
libnspr4-0d_4.8.7-0ubuntu1_i386.deb
to
libnspr4-0d_4.8.7-0ubuntu2_i386.deb

and my upgrade task stops in every try.

Any idea ?


Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/p/phonon-backend-xine/phonon-backend-xine_4.7.0really4.4.4-0ubuntu3_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/p/phonon-backend-xine/phonon-backend-xine_4.7.0really4.4.4-0ubuntu3_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda4/libgda-4.0-common_4.2.4-1ubuntu1_all.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda4/libgda-4.0-common_4.2.4-1ubuntu1_all.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda4/libgda-4.0-4_4.2.4-1ubuntu1_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda4/libgda-4.0-4_4.2.4-1ubuntu1_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nvclock/smartdimmer_0.8b4-1ubuntu6_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nvclock/smartdimmer_0.8b4-1ubuntu6_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb)
404 Not Found

---

### Post by MAFoElffen on 2011-06-15
> **wood9h said:**
> I just tried to upgrade, but seems that packages has changed from 
libnspr4-0d_4.8.7-0ubuntu1_i386.deb
to
libnspr4-0d_4.8.7-0ubuntu2_i386.deb

and my upgrade task stops in every try.

Any idea ?


Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/p/phonon-backend-xine/phonon-backend-xine_4.7.0really4.4.4-0ubuntu3_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/p/phonon-backend-xine/phonon-backend-xine_4.7.0really4.4.4-0ubuntu3_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda4/libgda-4.0-common_4.2.4-1ubuntu1_all.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda4/libgda-4.0-common_4.2.4-1ubuntu1_all.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda4/libgda-4.0-4_4.2.4-1ubuntu1_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda4/libgda-4.0-4_4.2.4-1ubuntu1_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nvclock/smartdimmer_0.8b4-1ubuntu6_i386.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nvclock/smartdimmer_0.8b4-1ubuntu6_i386.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb)
404 Not Found
Failed to fetch
[http://br.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb)
404 Not Found
I just download all the files you posted, so I know the repo's are active.  Have you verified your DNS connection?  Try this to verify that...
```

ping 72.14.213.104

```which is one of the current IP's for [www.google.com]("http://www.google.com")

---

### Post by wood9h on 2011-06-15
> **MAFoElffen said:**
> I just download all the files you posted, so I know the repo's are active.  Have you verified your DNS connection?  Try this to verify that...
```

ping 72.14.213.104

```which is one of the current IP's for [www.google.com]("http://www.google.com")

google is answering ping fine and quick.. my internet is ok.. 

seems that this Brazilian repository is without needed files !


Please check  [http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/](http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/)

it has a file [ibnspr4-0d_4.8.7-0ubuntu2_i386.deb]("http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu2_i386.deb")  and not libnspr4-0d_4.8.7-0ubuntu1_i386.deb .

Is there any way to set repository to another one ? or to tell upgrade manager that package now is number 2 and not number 1 ??


thanks in advance,

wood9h

This repository  br.archive.ubuntu.com  was setted automatically

---

### Post by wood9h on 2011-06-15
someone messed up brazilian repository

check the difference :

[http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/](http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/)

[http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/](http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/)

thats makes me unable to upgrade





> **wood9h said:**
> google is answering ping fine and quick.. my internet is ok.. 

seems that this Brazilian repository is without needed files !


Please check  [http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/](http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/)

it has a file [ibnspr4-0d_4.8.7-0ubuntu2_i386.deb]("http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu2_i386.deb")  and not libnspr4-0d_4.8.7-0ubuntu1_i386.deb .

Is there any way to set repository to another one ? or to tell upgrade manager that package now is number 2 and not number 1 ??


thanks in advance,

wood9h

This repository  br.archive.ubuntu.com  was setted automatically

---

### Post by MAFoElffen on 2011-06-15
> **wood9h said:**
> google is answering ping fine and quick.. my internet is ok.. 

seems that this Brazilian repository is without needed files !


Please check  [http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/](http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/)

it has a file [ibnspr4-0d_4.8.7-0ubuntu2_i386.deb]("http://br.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu2_i386.deb")  and not libnspr4-0d_4.8.7-0ubuntu1_i386.deb .

Is there any way to set repository to another one ? or to tell upgrade manager that package now is number 2 and not number 1 ??


thanks in advance,

wood9h

This repository  br.archive.ubuntu.com  was setted automatically
Go to System > Administration > Synaptic Package Manager > Settings > Repositories > Ubuntu Software Tab > Download From... It' a dropdown box that you select which server thr updates come from.

---

### Post by wood9h on 2011-06-15
> **MAFoElffen said:**
> Go to System > Administration > Synaptic Package Manager > Settings > Repositories > Ubuntu Software Tab > Download From... It' a dropdown box that you select which server thr updates come from.


Didnt work, It by passes my settings and marks br.archive.ubuntu.com

Someone must fix brazilian repository.. who must i contact ?

wood9h


Id solved it.. but br.archive still wrong..

I changed manually from synaptic settings, all from br.archive.ubuntu to us.archive.ubuntu  and Its installing right now.

Thanks for everyone for helping me.

wood9h

---


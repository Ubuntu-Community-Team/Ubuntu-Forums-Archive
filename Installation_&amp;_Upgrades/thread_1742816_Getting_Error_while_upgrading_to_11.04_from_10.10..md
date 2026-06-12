---
title: "Getting Error while upgrading to 11.04 from 10.10. Unable to proceed"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ninad.kochkar on 2011-04-29
Hi,

I am in Australia and my Server is mirror.optus.net. When I start upgrade process, it went fine for sometime but then I got the following errors:

[I]Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb](http://mirror.optus.net/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb) 403  Forbidden [IP: 211.29.132.60 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/p/phonon-backend-xine/phonon-backend-xine_4.7.0really4.4.4-0ubuntu3_i386.deb](http://mirror.optus.net/ubuntu/pool/universe/p/phonon-backend-xine/phonon-backend-xine_4.7.0really4.4.4-0ubuntu3_i386.deb) 404  Not Found [IP: 211.29.132.60 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/v/vala-0.10/valac-0.10_0.10.4-1ubuntu1_i386.deb](http://mirror.optus.net/ubuntu/pool/universe/v/vala-0.10/valac-0.10_0.10.4-1ubuntu1_i386.deb) 404  Not Found [IP: 211.29.132.60 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb](http://mirror.optus.net/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb) 404  Not Found [IP: 211.29.132.60 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb](http://mirror.optus.net/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb) 404  Not Found [IP: 211.29.132.60 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb](http://mirror.optus.net/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb) 404  Not Found [IP: 211.29.132.60 80][/I]

Even after closing, restarting and changing the server, I am continuously getting this error. Please let me know how to proceed from here.

Also, please let me know if there is any option to rollback the upgrade, so that I can change the Server. Currently, it is not taking effect, even if I change the Server.

---

### Post by Ghostlove on 2011-04-29
I am getting the same (well, a similar) error:

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb 403  Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb 403  Forbidden
```

Can anyone help us?

---

### Post by kavir1698 on 2011-04-29
I am also getting a similar error:

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb 403  Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb 403  Forbidden
```

---

### Post by zaphod2003 on 2011-04-29
Go to Synaptic package manager and edit sources and remove the gb. from all sources, then refresh.

Worked for me.

everything downloading and its currently updating.

---

### Post by kavir1698 on 2011-04-29
Would you please say how to edit sources and remove gb. from them?
thanks in advance

---

### Post by nightwolf2k5 on 2011-04-30
Thanks zaphod2003. That worked for me as well.
To change the source, you would have to go to System --> Administration --> Synaptic Package Manager.

Once there, go to Settings --> Repositories. And i think in other softwares tab, you can edit the entries there to remove the gb.

---

### Post by kavir1698 on 2011-04-30
Thank you, it worked for me as well.:)

---

### Post by Ghostlove on 2011-04-30
I appear to have got it working - changed my update source rather than removing the gb. from all sources, and it's got past the bit I was having trouble with. I'll update here if it doesn't work but so far, all looks good.

---

### Post by Iksf on 2011-05-02
Fixed here too, thought was gunna have to reinstall

---

### Post by nldquy on 2012-11-18
Sorry for my stupid question. But I really don't know what is " gb.  " source?

/Software Sources/Other Software and there's nothing like gb. in the list :(

---


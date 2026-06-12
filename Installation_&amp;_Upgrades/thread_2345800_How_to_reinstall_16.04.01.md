---
title: "How to reinstall 16.04.01"
date: 2016-12-08
forum: Installation &amp; Upgrades
---

### Post by stefanschmid on 2016-12-08
Dear all!

Due to several reasons, I would like to reinstall my Ubuntu 16.04.01  while keeping files and programs. But when I boot from USB, it doesn't  give me the reinstall option (see attachment) like described here: [http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot](http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot) and as can be seen  here: [URL="http://www.howtogeek.com/wp-content/uploads/2014/09/650x320xreinstall-ubuntu-while-keeping-files-and-programs.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.tNv2sjZKZg.png"]http://www.howtogeek.com/wp-content/uploads/2014/09/650x320xreinstall-ubuntu-while-keeping-files-and-programs.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.tNv2sjZKZg.png.

[/URL]Any ideas?

OS: ubuntu 16.04 LTS 64 Bit 
CPU: Intel® Core™ i5-5200U CPU @ 2.20GHz

[IMG]https://photos-1.dropbox.com/t/2/AAA4DEJxUSG95MB5DyhIzXatK_q0rkHcT4mbrQBEyLET7g/12/485097860/jpeg/32x32/1/_/1/2/IMG_20161207_205856.jpg/ELnUyPcDGJgqIAcoBw/M-aMwYOmOqGnpDmaePktRekw3jxM15oO8jinVpGgx4Q?size=2048x1536&size_mode=3[/IMG]

---

### Post by Jeroen_Mathon on 2016-12-08
stefanschmid,

Could you please elaborate on the reasons why you need a reinstall?
Because in most cases you cannot reinstall without overwriting all libraries and software.

---

### Post by karl96 on 2016-12-08
What is your partitioning layout like? It's possible if you have a separate /home and /usr partition to just reinstall system wide files just by reformatting the root partition.

---

### Post by howefield on 2016-12-08
Not quite what you are after but choosing the "*Something Else*" option will allow you to mount the partitions for installing over and keep your /home intact as long as you don't mark them for formatting. You would need to install any non default software afterwards but the configuration files in /home would still be there.

Goes without saying that you would want to have all important data backed up beforehand in any event.

---

### Post by stefanschmid on 2016-12-09
> **Jeroen_Mathon said:**
> stefanschmid,

Could you please elaborate on the reasons why you need a reinstall?
Because in most cases you cannot reinstall without overwriting all libraries and software.

Via Online Accounts my system was connected with my facebook and google account. I deleted that. But it seems that it is not entirely deleted. I face a problem while accessing [https://www.facebook.com/](https://www.facebook.com/) and [https://www.youtube.com](https://www.youtube.com) with eBlocker. Here is my detailed description: [http://user.forum.eblocker.com/topic/youtube-and-ssl-doesnt-word-other-https-do](http://user.forum.eblocker.com/topic/youtube-and-ssl-doesnt-word-other-https-do)

> **howefield said:**
> Not quite what you are after but choosing the "*Something Else*"  option will allow you to mount the partitions for installing over and  keep your /home intact as long as you don't mark them for formatting.  You would need to install any non default software afterwards but the  configuration files in /home would still be there.

Goes without saying that you would want to have all important data backed up beforehand in any event.

Thanks. I might try that.

> **karl96 said:**
> What is your partitioning layout like? It's possible if you have a separate /home and /usr partition to just reinstall system wide files just by reformatting the root partition.

Thanks. I will check that.

---


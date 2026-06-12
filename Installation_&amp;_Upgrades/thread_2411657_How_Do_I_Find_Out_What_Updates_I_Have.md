---
title: "How Do I Find Out What Updates I Have?"
date: 2019-02-02
forum: Installation &amp; Upgrades
---

### Post by HerzeleidMeister on 2019-02-02
How/where do I find the information about what the Laptop updated just a day ago? It came up and said that there was an update and I ran the update and it ran just fine, installed etc. I had to restart. Once I did that it seemed fine. When I shut the laptop down for the night and then turned it back on in the AM, now there are weird little annoying things happening that were not happening before the update. 

***Running:*** Ubuntu 18.04 on a Lenovo Y40-70 with 16 GB RAM & 2.0 CPU. 

Update was yesterday, or the day before and I have not changed anything or updated anything since.

***Weird Annoyances Now: ***The Dock Bar sometimes will not auto hide now. It worked fine before. It seems to take longer to boot up. Before it would immediately add the desktop icons, now it takes about a minute. It seems a little slower now as well.

---

### Post by Impavidus on 2019-02-02
It's in the log files. Have a look at /var/log/dpkg.log (the latest) and /var/log/dpkg.log.1 (the one before). With standard settings, a fresh log file is started every month and old logs are kept for a year. Those of more than a month old get compressed to save some disk space.

---

### Post by Dennis N on 2019-02-02
All the update transactions are recorded in text files stored in /var/log/apt/

history.log is the most recent, while earlier files are archived: history.log.1.gz is next most recent, then history.log.2.gz and so on. For the .gz archive files you need to extract the actual record file from the archive to read it.

---

### Post by HerzeleidMeister on 2019-02-05
Thanks all, I'll have a look. Things seem to be running normally again.

---


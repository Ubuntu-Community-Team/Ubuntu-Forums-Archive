---
title: "Partitioning to Accommodate Ubuntu One"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by leehach on 2012-06-24
I'm about to upgrade to either Precise or Linux Mint Maya. For the last few years I have used the three-partition scheme with / /home and /data. The user folders like Documents, Music, etc. are all symlinks to /data so that I can blow away / or /home at any time without touching my personal documents.

I've been curious to try Ubuntu One, but haven't because it only backs up/syncs in /home and won't follow links. So now I'm considering partially or completely merging my data into /home. My questions are:

(a) Is there a way to make Ubuntu One work with my data directory? For example, what if I loaded my data partition at /home/data (instead of /data). 

(b) My data partition contains other stuff that I normally wouldn't put in home like a postgres cluster and some large files files that I don't want backed up and want to otherwise keep segregated from the rest of my documents. Is it (a) possible, (b) wise to start creating other folders (e.g. /postgres_data) as subfolders of /home?

Using Ubuntu One seems interesting but not crucial (I have another cloud based backup), so if there's no solution, oh well, but I'm curious to know if there's a way to do this.

--Lee

---


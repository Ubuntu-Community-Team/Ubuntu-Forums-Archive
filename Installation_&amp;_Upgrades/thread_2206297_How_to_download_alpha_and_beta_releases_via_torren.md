---
title: "How to download alpha and beta releases via torrent?"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by Anand.Kumar on 2014-02-18
I can't download the whole ISO image of Ubuntu OS (Alpha/Beta) in one session. Is there any alternative like torrents (strongly looking for this) OR any download manager which may work (pause/resume).

Thanks.

---

### Post by ian-weisser on 2014-02-18
Good old wget, included with the default install of Ubuntu, will happily resume downloads.

```
$ wget http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso             # Start download
Saving to: &#8216;trusty-desktop-i386.iso&#8217;
 0% [                                       ] 1,151,678    163KB/s  eta 1h 50m
^C                                                                                      # Stop download with CTRL+C


$ ls -l | grep trusty
-rw-r--r--  1 ian  ian           1186238 Feb 18 10:04 trusty-desktop-i386.iso           # Incomplete download saved


$ wget --continue http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso  # Use --continue flag to resume download
Saving to: &#8216;trusty-desktop-i386.iso&#8217;
[Download resumes]

```

Much testing has moved from alpha/beta versions to daily snapshots.

---

### Post by sudodus on 2014-02-18
Another alternative is zsync, which will work nicely once you have one good version of the ubuntu iso file. See this link (example for trusty-desktop-amd64.iso)

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/63058/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/63058/downloads)

With the zsync command line you need *only download what changed* from the previous download.

```
zsync http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync
```

I think you must also install zsync

```
sudo apt-get install zsync
```

---

### Post by Anand.Kumar on 2014-02-19
Thanks for your replies. I didn't know about zsync and --continue command in wget! It's great. 

I still have a doubt. Isn't the ISO image file changes everyday? What will happen if the file changed if I have downloaded half of it?

---

### Post by ian-weisser on 2014-02-19
Good point. Check the upload time on the web page to be sure you are still downloading the same version. "Daily" does not guarantee "once each day at the same time." It's a testing snapshot; sometimes it's down, sometimes it fails to boot, sometimes it get respun multiple times in one day to address a critical bug, sometimes the daily is delayed by a few hours.

It may be worthwhile to plan an longer or higher-speed connection session (at a cafe, for example) to get the entire file at once. Or perhaps you may consider using a stable release instead of a testing version.

---

### Post by sudodus on 2014-02-19
> **Anand.Kumar said:**
> Thanks for your replies. I didn't know about zsync and --continue command in wget! It's great. 

I still have a doubt. Isn't the ISO image file changes everyday? What  will happen if the file changed if I have downloaded half of it?

I have no own experience, but I think ***zsync*** can cope with it.

-o-

Good old ***rsync*** is another powerful alternative for example with the option **--partial**. From ```
man rsync
```

```
       --partial
              By  default,  rsync will delete any partially transferred file if the transfer is inter&#8208;
              rupted. In some circumstances it is more desirable to keep partially transferred  files.
              Using the --partial option tells rsync to keep the partial file which should make a sub&#8208;
              sequent transfer of the rest of the file much faster.

       --partial-dir=DIR
              A better way to keep partial files than the --partial option is to specify  a  DIR  that
              will  be  used  to  hold  the partial data (instead of writing it out to the destination
              file).  On the next transfer, rsync will use a file found in this dir as data  to  speed
              up the resumption of the transfer and then delete it after it has served its purpose.

              Note  that if --whole-file is specified (or implied), any partial-dir file that is found
              for a file that is being updated will simply be removed (since rsync  is  sending  files
              without using rsync&#8217;s delta-transfer algorithm).

              Rsync  will  create  the DIR if it is missing (just the last dir -- not the whole path).
              This makes it easy to use a relative path (such  as  "--partial-dir=.rsync-partial")  to
              have rsync create the partial-directory in the destination file&#8217;s directory when needed,
              and then remove it again when the partial file is deleted.

              If the partial-dir value is not an absolute path, rsync will add an exclude rule at  the
              end  of  all  your  existing excludes.  This will prevent the sending of any partial-dir
              files that may exist on the sending side, and will also prevent the untimely deletion of
              partial-dir  items  on  the  receiving side.  An example: the above --partial-dir option
              would add the equivalent of "-f '-p .rsync-partial/'" at the end  of  any  other  filter
              rules.

              If   you  are  supplying  your  own  exclude  rules,  you  may  need  to  add  your  own
              exclude/hide/protect rule for the partial-dir because (1) the  auto-added  rule  may  be
              ineffective  at  the  end  of  your other rules, or (2) you may wish to override rsync&#8217;s
              exclude choice.  For instance, if you want to make rsync  clean-up  any  left-over  par&#8208;
              tial-dirs  that  may be lying around, you should specify --delete-after and add a "risk"
              filter  rule,  e.g.   -f  'R  .rsync-partial/'.    (Avoid   using   --delete-before   or
              --delete-during unless you don&#8217;t need rsync to use any of the left-over partial-dir data
              during the current run.)

              IMPORTANT: the --partial-dir should not be writable by other users or it is  a  security
              risk.  E.g. AVOID "/tmp".

              You can also set the partial-dir value the RSYNC_PARTIAL_DIR environment variable.  Set&#8208;
              ting this in the environment does not force --partial  to  be  enabled,  but  rather  it
              affects  where  partial  files go when --partial is specified.  For instance, instead of
              using  --partial-dir=.rsync-tmp  along  with  --progress,  you  could   set   RSYNC_PAR&#8208;
              TIAL_DIR=.rsync-tmp  in  your environment and then just use the -P option to turn on the
              use of the .rsync-tmp dir for partial transfers.  The  only  times  that  the  --partial
              option  does  not  look  for this environment value are (1) when --inplace was specified
              (since --inplace conflicts with --partial-dir), and (2) when --delay-updates was  speci&#8208;
              fied (see below).

              For the purposes of the daemon-config&#8217;s "refuse options" setting, --partial-dir does not
              imply --partial.  This is so that a refusal of the --partial option can be used to  dis&#8208;
              allow the overwriting of destination files with a partial transfer, while still allowing
              the safer idiom provided by --partial-dir.

       --delay-updates
              This option puts the temporary file from each updated  file  into  a  holding  directory
              until  the  end  of  the transfer, at which time all the files are renamed into place in
              rapid succession.  This attempts to make the updating of the files a little more atomic.
              By  default the files are placed into a directory named ".~tmp~" in each file&#8217;s destina&#8208;
              tion directory, but if you&#8217;ve specified the --partial-dir option, that directory will be
              used  instead.   See  the  comments in the --partial-dir section for a discussion of how
              this ".~tmp~" dir will be excluded from the transfer, and what you can do  if  you  want
              rsync to cleanup old ".~tmp~" dirs that might be lying around.  Conflicts with --inplace
              and --append.

              This option uses more memory on the receiving side (one bit per  file  transferred)  and
              also requires enough free disk space on the receiving side to hold an additional copy of
              all the updated files.  Note also that you should not use an  absolute  path  to  --par&#8208;
              tial-dir  unless  (1)  there is no chance of any of the files in the transfer having the
              same name (since all the updated files will be put into a single directory if  the  path
              is  absolute)  and  (2)  there  are  no mount points in the hierarchy (since the delayed
              updates will fail if they can&#8217;t be renamed into place).

              See also the "atomic-rsync" perl script in the "support" subdir for an update  algorithm
              that is even more atomic (it uses --link-dest and a parallel hierarchy of files).

```

---

### Post by sudodus on 2014-02-19
> **ian-weisser said:**
> Good point. Check the upload time on the web page to be sure you are still downloading the same version. "Daily" does not guarantee "once each day at the same time." It's a testing snapshot; sometimes it's down, sometimes it fails to boot, sometimes it get respun multiple times in one day to address a critical bug, sometimes the daily is delayed by a few hours.

It may be worthwhile to plan an longer or higher-speed connection session (at a cafe, for example) to get the entire file at once. Or perhaps you may consider using a stable release instead of a testing version.

+1

---


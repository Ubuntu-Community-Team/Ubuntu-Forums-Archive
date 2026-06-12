---
title: "apt-mirror seems to skip &lt;release&gt;-proposed/main/dist-upgrader-all"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by jejones3141 on 2010-06-03
Where I work there are a number of workstations set up to run Ubuntu. We set up apt-mirror to retrieve copies of Karmic repositories so we could save coworkers time and also cut down overall load in the repositories (one copy beats dozens). We mirrored the repositories that /etc/apt/sources.list referred to, edited said file to point at our mirror, made sources.list files point at our mirror, and all was well... but now, Lucid Lynx is official, and as we now know (thanks to [http://blog.knuthaugen.no/2009/12/doing-do-release-upgrade-on-an-offline-ubuntu-mirror.html]("http://blog.knuthaugen.no/2009/12/doing-do-release-upgrade-on-an-offline-ubuntu-mirror.html"), we have to have the karmic-proposed tree, which has the upgrader, (and we have to modify the metarelease files as well). Easy enough, right? Just extend the list of stuff to mirror and let it retrieve the needed files.

But... while we see the karmic-proposed directory in what apt-mirror is now retrieving, we don't see the dist-upgrader-all and installer* directories. apt-mirror does recursively grab all the stuff underneath what one tells it to fetch, right?

UPDATE: The reason is probably that I didn't tell it to get those subdirectories; the line for karmic-proposed needs to ask for dist-upgrader and installer. I will add the correct lines to this message and mark it solved once I verify that this works as expected.

UPDATE: Apparently others have the same problem; see [http://www.supportsages.com/blog/2010/05/how-to-create-a-local-ubuntu-repository-updateupgrade-distros-locally-and-thereby-save-bandwidth/](http://www.supportsages.com/blog/2010/05/how-to-create-a-local-ubuntu-repository-updateupgrade-distros-locally-and-thereby-save-bandwidth/) for details. I will follow the method described there.

---


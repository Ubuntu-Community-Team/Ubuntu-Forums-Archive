---
title: "How to not enable SSH in Ubuntu 9.0.2 version"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by sbhavra on 2010-06-17
[COLOR=#810081]Hi,[/COLOR]

[COLOR=#810081]I am installing Ubuntu 9.0.2 begineer version and when i connect access this server remotely it is not having SSH enabled. [/COLOR]
[COLOR=#810081]Does the ubuntu 10.0 server is having SSH enabled?[/COLOR]
[COLOR=#810081]Please suggest me what to do for this(any settings/third party tool).[/COLOR]

[COLOR=#810081]Regards,[/COLOR]
[COLOR=#810081]Suukhbir[/COLOR]

---

### Post by lechien73 on 2010-06-17
Do you mean you're installing Ubuntu 9.04?

If you want to set-up an SSH server on Ubuntu, then it's quite straightforward.

sudo apt-get install ssh

This installs the packages needed for the ssh server and client.

More information can be found here:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Setup_an_SSH_server](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Setup_an_SSH_server)

Hope this helps - sorry if I've misunderstood your question.

---


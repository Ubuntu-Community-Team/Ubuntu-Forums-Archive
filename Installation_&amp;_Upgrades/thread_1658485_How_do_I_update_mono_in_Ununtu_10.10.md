---
title: "How do I update mono in Ununtu 10.10?"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by krazy76 on 2011-01-02
Hello everyone! What I am trying to figure out is how would I go about updating mono in Ubuntu 10.10? I have small knowledge in linux so as simple as possible please :). I have tried purging mono and reinstalling with the directions from [http://www.integratedwebsystems.com/2010/12/mono-2-8-1-install-script-for-ubuntu-and-fedora/](http://www.integratedwebsystems.com/2010/12/mono-2-8-1-install-script-for-ubuntu-and-fedora/) but when I check the version with mono -V the version in use is 2.6.7.

Any help with this would be great.

[EDIT]

I have been able to get Mono to update to the latest and everything is running good still. When I run mono --version the latest one is in use 2.8.2. Now I do have one problem I am sure some one can answer. When I set apache2 to run with the latest with "LoadModule mono_module /opt/mono-2.8.2/bin/mod-mono-server4" I get a syntax error in the apache2.conf and mono.conf along with "cannot load /opt/mono-2.8.2/bin/mod-mono-server4 into server: /opt/mono-2.8.2/bin/mod-mono-server: invalid ELF header.

Any ideas how to get rid of this error?

---


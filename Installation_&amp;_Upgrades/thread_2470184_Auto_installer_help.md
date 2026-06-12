---
title: "Auto installer help"
date: 2021-12-21
forum: Installation &amp; Upgrades
---

### Post by ender8282 on 2021-12-21
I'm trying to setup an auto-installer.  I'm using the script that I found [here]("https://github.com/covertsh/ubuntu-autoinstall-generator") and I've gotten pretty close with the following config:
```

autoinstall:
  version: 1
  #interactive-sections:
  #  - identity
  ssh:
    install-server: true
  identity:
    hostname: hostname
    username: user
    password: "$6:$##########"
  late-commands:
    - curl -L https://bootstrap.saltproject.io -o /target/tmp/salt-bootstrap.sh
    - curtin in-target --target=/target -- bash /tmp/salt-bootstrap.sh -A salt-master -X

```

That all works as expected.  I boot my VM with the generated iso attached, the OS gets installed, salt gets installed, it reboots and is ready to go!  

Next up I tried adding the bits necessary to use a repo mirror:
```

  ...
  #  - identity
  apt:
    primary:
      - arches [default]
        uri: http://my-mirror/ubuntu/mirror/archive.ubuntu.com/ubuntu/
  ssh:
  ...

```

With the apt config added the whole process becomes interactive and nothing is pre-populated.  Comment out those 4 lines and everything works as expected.  

Has anyone else experienced problems specifying an apt mirror?  The syntax feels really weird to me but it matches the example I found [here]("https://ubuntu.com/server/docs/install/autoinstall-reference#apt").  I'd love to see other working auto-install config examples; my google-fu hasn't turned up many.

---

### Post by MAFoElffen on 2021-12-22
There s a part I think you "missed" and overlooked... You omitted a directive. You added a link to it from where you used an example... which the line in red (below was explained at another link from there, further link, which it stated it was so important that it deserved it's own section...
```

apt:     [COLOR=#b22222]preserve_sources_list: false[/COLOR]
    primary:
        - arches: [i386, amd64]
          uri: "http://archive.ubuntu.com/ubuntu"
        - arches: [default]
          uri: "http://ports.ubuntu.com/ubuntu-ports"
    geoip: true

```
What you overlooked is that curtin's default is "True"... In other words, it's default is to preserve the sources list and leave it as is...
> 
 **Interpretation / Meaning**

 curtin reads preserve_sources_list to indicate whether or not it should update the target systems&#8217; /etc/apt/sources.list.  This includes replacing the mirrors used (apt/primary&#8230;).
 cloud-init reads preserve_sources_list to indicate whether or not it should *render* /etc/apt/sources.list from its built-in template.
 
  **defaults**

 Just for reference, the preserve_sources_list defaults in curtin and cloud-init are:[INDENT] 
[LIST]
[*]curtin: **true** By default curtin will not modify /etc/apt/sources.list in the installed OS.  It is assumed that this file is intentionally as it is. 
[*]cloud-init: **false** 
[*]cloud-init in ephemeral environment: **false** 
[*]cloud-init system installed by curtin: **true** (curtin writes this to a file /etc/cloud/cloud.cfg.d/curtin-preserve-sources.cfg  in the target).  It does this because we have already written the  sources.list that is desired in the installer.  We do not want  cloud-init to overwrite it when it boots. 
[/LIST]
 
[/INDENT]

I think if you add 'preserve_sources_list: false' back into your yaml file, that it will respect this section.

---

### Post by ender8282 on 2022-01-03
Thanks for the answer.  Adding the preserve_sources_list: false (along with a missing colon following arches) seems to have done the trick.  The auto-installer now appears to work save what I believe is a misconfiguration in my repo mirror.

---


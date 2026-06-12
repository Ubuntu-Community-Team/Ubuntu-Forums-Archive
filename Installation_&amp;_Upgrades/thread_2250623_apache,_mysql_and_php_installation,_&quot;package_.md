---
title: "apache, mysql and php installation, &quot;package is missing&quot;"
date: 2014-10-29
forum: Installation &amp; Upgrades
---

### Post by ale13 on 2014-10-29
Hello,

I am trying to install apache, mysql and php on my ubuntu 14.04 but anytime that I run 

#sudo apt-get install apache2, I am havis this issue

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libapache2-mpm-itk

E: Package 'apache2' has no installation candidate


```

so I try this,

#sudo apt-get install libapache2-mpm-itk

and I get;

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libapache2-mpm-itk : Depends: apache2-api-20120211 but it is not installable
E: Unable to correct problems, you have held broken packages.

```


any help or sugesttion what can I do to solve this problem?

Thank in advanced

---


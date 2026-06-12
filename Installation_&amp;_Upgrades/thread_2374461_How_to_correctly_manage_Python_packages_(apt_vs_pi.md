---
title: "How to correctly manage Python packages (apt vs pip)"
date: 2017-10-16
forum: Installation &amp; Upgrades
---

### Post by raptorista2 on 2017-10-16
Hi everybody. I'm running Ubuntu 16.04 and I recently run into problems with my Python packages; while searching for a solution I came across multiple sources advising to prefer installing packages with pip instead of apt, and even more sources advising not to mix the two installation methods, so I decided to clean my system which currently has python packages installed both ways. Easier said than done, I came up with several questions on best practices for a good system management.
There exists at least one python package that I need and I cannot find in Ubuntu's repos, so I decided to try to uninstall of all the python packages that I installed from apt and install the corresponding pip packages, but this turns out to break other packages' dependencies, so I arrived to the following stalemate:

[LIST=1]
[*]I want package meshio which is available in pip but not in apt. This package I need only for a restricted use in a specific project. 
[*]Package numpy, currently in apt and available in pip, is a dependency of another application, e.g. Paraview, that I can't get from pip, so uninstalling apt::numpy in favor of pip::numpy would remove Paraview, which instead I need. 
[*]Package petsc4py is only available in pip and depends on petsc at a version available in pip but not in apt, but I already have apt::petsc and I need it for some other stuff, so installing pip::petsc4py would result in the installation of pip::petsc alongside apt::petsc [at a different version]. 
[/LIST]

These are my biggest problems right now. As far as solutions are concerned, my ideas are
[LIST=1]
[*]Keep in apt all python packages that are dependencies of non-python packages [e.g. paraview]; remove all apt packages that I installed manually;  install the pip version of all packages that I need, including those that I keep in apt. This solution implies duplicating  packages. 
[*]Keep in apt all python packages that are dependencies of non-python  packages [e.g. paraview]; remove all apt packages that I installed  manually and  install the pip version of only these packages that I need. This solution still results in duplicating  packages which are dependencies of both packages in apt and packages in pip. 
[*]Remove all python packages from apt, manually compile applications that are removed from apt as a consequence and link them to the python packages installed by pip. This goes against having a repository and I would really like to avoid this. 
[*]Virtual environments. I have a not-too-precise understanding of what this is, but the idea would be to remove all pip packages, keep all apt python packages that are dependencies of non-python  packages and then create a virtualenv for every python project that I do and needs special dependencies not provided by apt. My understanding is that in this case a virtualenv could benefit packages installed from apt and pip would be used to complement the packages that are at the wrong version. This looks like the cleanest solution, although I have no experience with virtual environments and I will have to learn to use them. 
[/LIST]

What is the correct way to deal with this situation? Any other solution is welcome.

Thanks in advance for any help.

---

### Post by TheFu on 2017-10-19
TL;DR.

It is simple.
* Custom developed code should be self contained.  The version and libraries used should be part of the web-app/program environment.  If you need python 55.87.32, then you should have that installed and any libraries should be tied to that installation. Your code should too.

* System code should use the system versions of everything. That means using apt-get/apt/aptitude/synaptic or whatever other interface you choose to manage APT on the system.  If you want to make system-level tools, then you should use these same libraries as dependencies in your packaging.

* Python, ruby, perl, all have ways to keep whole production environments separate from the system-installed versions.  perl uses perlbrew.  Ruby uses rbenv or rvm. Python has a few options too.  

* For any 3rd party libraries (usually in different languages), then you need the same separation.    System stuff gets installed using APT.  None system stuff gets installed and managed as separate dependencies - usually into /usr/local/   There's a tool called epkg that does this in a semi-automatic way.  I'm not a fan, much prefer to just manage these things with symbolic links and {insert-program}_HOME env variables, as needed.

As an example, I have 4 different versions of Perl installed on my development machines.  Switching between each for a specific process is trivial - basically, it just changes the PERLIB5, MANPATH and PATH env variables.

JAVA_HOME ... is something similar that Java people have used for decades.  Same-same.


As for virtual environments, that has many different meanings dependent on your understanding.  Until you nail that down a little, we cannot have a conversation.  For example, a "virtual host" can mean many different things.
* virtual machine (xen, kvm, virtualbox) host system
* virtual private server ... really a VM-client, but some people call them "virtual hosts"
* container setup / Docker / lxd / lxc / Juju ... could be a virtual host.
* Webservers like apache, nginx, and others have a way to use the DNS-name as a way to request different virtual web-sites. Someone could call this a "virtualhost"  - mainly because the geniuses at Apache decided to name the configuration directive <VirtualHost *:80>.  In fairness, Apache was probably the most popular tool using this long before it became common, but virtual machines have been around since the 1970s in the mainframe world, so that really isn't much of an excuse.

Anyways, there is good reason for confusion, especially with all the similar meanings for the same words.

---

### Post by raptorista2 on 2017-10-23
Hi, thank you for your reply.

I'm not sure I correctly understand your point 1: is your suggestion  to keep everything that is not repository-provided into a sandbox?

Your point 4 seems to refer to what I do with pip, that is to install everything that I need system-wide, but what about needing a different version from the system-provided one? Should I create a duplicate installation system-wide?

A far as virtual environments are concerned, I was thinking of Python's virtualenv or virtualenvwrapper or one of these, meaning to have missing dependencies installed next to the source folder and adjusting environment variables coding a particular project.

---

### Post by TheFu on 2017-10-23
Anything installed via pip should be into a non-system-wide area, managed by env vars.

"Sandbox" can mean all sorts of different things. I'm suggesting just managing different python dev/prod areas using environment vars only, no need for cnames or other container-like limitations from the kernel.  

Python has tools that handle the environment stuff in a smart way, I'm positive. No need to re-invent that wheel.

For system tools, use apt to install any python dependencies.

For non-system tools or webapps, use the python version manager tool (whatever it is called) to keep the python binary and any desired python libraries separate from the system python stuff.  You want something that lets you have 5 different versions of python with 5 different dependency library areas and 5 different web-app areas.  THAT is the professional solution.

I'm a perl guy, so ... 
```
$ perlbrew list
  perl-5.20.1 (5.20.3)
* perl-5.22.1
  perl-5.26.0

```  There are 3 versions of perl on my laptop and 5.22.1 is "active" ... since that's the environment I need right now for a project.  Any OS installed packages that need perl, use the system-perl, not my special areas.

I googled the python tool - **pyenv** is what you want.  Find a 3min youtube video on using it, if you learn that way.

---

### Post by raptorista2 on 2018-03-05
Hi, thanks for your explanation. In the end I did more or less what you suggested, using virtualenv instead of pyenv. I don't have time to learn all the ways of the various alternatives, and virtualenv looks easy enough to be used without really knowing what I'm doing, which is a good compromise for now.

---


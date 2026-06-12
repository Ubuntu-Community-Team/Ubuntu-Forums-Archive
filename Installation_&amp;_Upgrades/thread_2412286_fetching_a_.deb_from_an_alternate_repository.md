---
title: "fetching a .deb from an alternate repository"
date: 2019-02-10
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2019-02-10
is there a direct "one command" way to fetch a .deb file from an alternate repository named on an apt-add-repository without actually adding a (that) repository to your sources, like maybe a direct URL download from that repository?

rephrasing the question:

based on many useless answer google found for me and the way some of them were asked:

given the name (or hostname) of a debian/ubuntu repository, and a package name (and architecture and distro version), is there a way to construct an HTTP URL that can be fetched to download the .deb file?  i might like to download it in a user that has no sudo privileges and/or on a different host.

i am NOT wanting any suggestions for tool to download files based on URLs.  i already have such a tool that does what else i need.

---

### Post by tea for one on 2019-02-11
Do you have synaptic package manager installed?

When you mark a package for installation, you can generate a download script via the file menu.

The script uses wget as in the following example:-

> wget -c [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_7.6p1-4ubuntu0.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_7.6p1-4ubuntu0.2_amd64.deb)

Here is the website for wget:- [https://www.gnu.org/software/wget/](https://www.gnu.org/software/wget/)

Any help?

---

### Post by again? on 2019-02-11
....and this page details how to find a direct link to a deb file from a ppa and an example script to construct a URL from the ppa.
[https://askubuntu.com/questions/618242/how-can-i-download-deb-from-a-ppa](https://askubuntu.com/questions/618242/how-can-i-download-deb-from-a-ppa)

---


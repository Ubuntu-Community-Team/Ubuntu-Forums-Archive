---
title: "Unresolved Dependencies Koha ILS"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by umfunix on 2012-11-28
Hi

I'm trying to install Koha ILS following the instructions on [koha-community]("http://wiki.koha-community.org/wiki/koha_on_ubuntu_-_packages") wiki but keep ons getting this error...
> This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.  The following packages have unmet dependencies.

Apt-get does indicate which dependencies, but it looks as if I do have some of those dependencies installed.  Apt-get says:
> Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 koha-common : Depends: libchi-driver-memcached-perl but it is not going to be installed
               Depends: libchi-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
I also tried to solve the dependencies to see if I an install them seperatel, but the same error occurred when trying to install libchi-perl.  

Any help getting out of this dependancy hell and get Koha installed?

---

### Post by umfunix on 2012-11-29
Hey, am I alone in this..?

---

### Post by ashijit007 on 2012-12-13
@umfunix

I had the same issue. Just follow these steps and it should work:

sudo rm /etc/apt/sources.list.d/koha.list

sudo apt-get update
sudo apt-get install libchi-driver-memcached-perl
sudo apt-get install libdigest-jhash-perl
sudo cpan install Data::Pagination

Now go back to this line in the installation instructions, and continue the installation.  

echo deb [http://debian.koha-community.org/koha](http://debian.koha-community.org/koha) squeeze main | sudo tee /etc/apt/sources.list.d/koha.list 

Found the solution here: [http://koha.1045719.n5.nabble.com/Problem-with-install-Koha-packages-on-ubuntu-server-12-04-amd64-td5734983.html](http://koha.1045719.n5.nabble.com/Problem-with-install-Koha-packages-on-ubuntu-server-12-04-amd64-td5734983.html)

---


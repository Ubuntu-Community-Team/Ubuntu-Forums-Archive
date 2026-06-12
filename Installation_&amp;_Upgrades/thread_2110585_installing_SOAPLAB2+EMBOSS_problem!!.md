---
title: "installing SOAPLAB2+EMBOSS problem!!"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by xiangwulu on 2013-01-30
Hi all,

i tried to install soaplab2+emboss on amazon web service instance, 

i got java, ant, maven, tomcat installed, built soaplab2 firstly, it can be accessed at:[http://ec2-176-34-220-249.eu-west-1.compute.amazonaws.com:8080/soaplab2/]("http://ec2-176-34-220-249.eu-west-1.compute.amazonaws.com:8080/soaplab2/"), 

and then i install emboss followed this site: [http://soaplab.sourceforge.net/soaplab2/EmbossNotes.html]("http://soaplab.sourceforge.net/soaplab2/EmbossNotes.html")

but for the step "**ant genemboss**", i got such error message:

```
[acd2xml] Processing digest...
  [acd2xml]     using /root/soaplab2/EMBOSS-6.5.7/share/EMBOSS/acd/digest.acd
  [acd2xml] ERROR: Modification of non-creatable array value attempted, subscript -1 at acd.y line 575.
  [acd2xml]

BUILD FAILED
/root/soaplab2/soaplab2/xmls/emboss.xml:75: The following error occurred while executing this line:
/root/soaplab2/soaplab2/xmls/acd2xml.xml:58: exec returned: 1
```

i searched on the internet for the similar error message but not much information useful. 

would anyone help? thanks so much!!

---

### Post by xiangwulu on 2013-01-31
probably i should state my problems bit more clear:
i am trying to install soaplab2 + emboss on amazon web service.


I used the installation instruction from:
[http://soaplab.sourceforge.net/soaplab2/BuildGuide.html]("http://soaplab.sourceforge.net/soaplab2/BuildGuide.html") soaplab2 installation

[http://soaplab.sourceforge.net/soaplab2/EmbossNotes.html]("http://soaplab.sourceforge.net/soaplab2/EmbossNotes.html") emboss installation

I installed java jdk, tomcat, ant, soaplab and emboss on the cloud instance.

The emboss commands worked on the local terminal window ( wossname), but not the server(-bash: wossname: command not found)

here is the my public server address:
[http://ec2-176-34-220-249.eu-west-1.compute.amazonaws.com:8080/soaplab2/]("http://ec2-176-34-220-249.eu-west-1.compute.amazonaws.com:8080/soaplab2/")

this is the error message returned after I run "ant genemboss" command, and i get this error both when i set up soaplab+emboss on local PC and cloud instance:
```
[acd2xml] Processing digest...
[acd2xml] using /root/soaplab2/EMBOSS-6.5.7/share/EMBOSS/acd/digest.acd
[acd2xml] ERROR: Modification of non-creatable array value attempted, subscript -1 at acd.y line 575.
[acd2xml]
```

```
BUILD FAILED
/root/soaplab2/soaplab2/xmls/emboss.xml:75: The following error occurred while executing this line:
/root/soaplab2/soaplab2/xmls/acd2xml.xml:58: exec returned: 1
```

acd2xml.xml  line 58 is: <exec executable="perl" taskname="acd2xml" failonerror="true">


here are my build.properties file:
```

# If you want to specify some local properties that will be used by
# Ant tasks, copy this file into 'build.properties' and edit it as you
# need.
#
# $Id: build.properties.template,v 1.16 2009/06/26 09:56:00 mahmutuludag Exp $
# --------------------------------------------------------------------
# --------------------------------------------------------------------
# Pointer to your own templates of Soaplab configuration files
# --------------------------------------------------------------------
my.soaplab.properties = testing.soaplab.properties
#my.soaplab.client.properties = testing.soaplab.client.properties
#my.log4j.properties = testing.log4j.properties
# --------------------------------------------------------------------
# Full path to your Tomcat installation.
# --------------------------------------------------------------------
tomcat.home=/etc/tomcat6
# --- Where is your Tomcat listening
tomcat.port = 8080
tomcat.host = ec2-176.34.220.249.eu-west-1.compute.amazonaws.com
# --- For using Tomcat manager to deploy
#tomcat.manager.username = tomcat
#tomcat.manager.password = tomcat
#tomcat.manager.url= http://my.tomcathost:9800/manager
# --------------------------------------------------------------------
# For deploying services to Tomcat
# --------------------------------------------------------------------
# To use metadata (etc.) from other directories than the ones "embedded"
# in the Tomcat webapps structure:

#server.metadata.dir = /root/soaplab2/soaplab2/metadata/generated
#server.runtime.dir  = /root/soaplab2/soaplab2/_R_
#server.scripts.dir  = /root/soaplab2/run
catalina.base=/var/lib/tomcat6
# --------------------------------------------------------------------
# These properties are for those who wish to use their own, additional
# classes, for the Soaplab2 services. If you write a Soaplab2 plugin,
# these properties are for you.
#
# The classes you wish to add must be packed, usually as jars. The
# directory with the jar files is given by the property
# user.lib.dir. Additionally, a pattern which jars to use can be
# specified by the property user.lib.include.
# --------------------------------------------------------------------
#user.lib.dir =
#user.lib.include = *.jar
# --------------------------------------------------------------------
# Configuring Spinet web client
# --------------------------------------------------------------------
#soaplab.docs.url = http://localhost/~senger/soaplab2/
#local.contact = &lt;a href=&quot;mailto:martin.senger&#64;gmail.com&quot;&gt;Martin Senger&lt;/a&gt;
spinet.welcome.msg = Soaplab at CIT
# --------------------------------------------------------------------
# Specifically for those who are using EMBOSS
# --------------------------------------------------------------------
emboss.home = /root/soaplab2/EMBOSS-6.5.7
emboss.supplier = CIT
emboss.version = 6.5.7
# --------------------------------------------------------------------
# Set how to compile Java source to Java classes
# --------------------------------------------------------------------
#compile.verbose = false
#compile.deprecation = false
#compile.optimize = false
#compile.warnings = true
# -----------------------------------------------------------------------------------------
# For those who prefers additional WSDL files with strongly typed input/output descriptions
# -----------------------------------------------------------------------------------------
#typedinterface.enable = true
====================================================

```

Thanks!!

---

### Post by xiangwulu on 2013-02-05
the above issues is the error i saw the most times. i deleted **digest.acd** and then it built ok. but i didn't know the reason of this, i didn't change this file after downloaded and unpacked. 

this is my aws server address:
[http://ec2-176-34-220-249.eu-west-1.compute.amazonaws.com:8080/soaplab2]("http://ec2-176-34-220-249.eu-west-1.compute.amazonaws.com:8080/soaplab2")

i run the **ant genemboss** successful, and in soaplab2 directory run 
**ant jaxdeploy** to deploy the emboss services(edited the config file), but this spinet page still didn't show emboss web services(like the one show here: [http://soaplab.sourceforge.net/soaplab2/SpinetClient.html]("http://soaplab.sourceforge.net/soaplab2/SpinetClient.html")). 
 
has anyone came cross the similar problem? any help is appreciated.

---


---
title: "xls2csv works on local but not on remote"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by cheerPuncH on 2012-07-31
Hi,

I installed the python module pyExcelerator on my local Ubuntu (the latest LTS) and the following works fine.
```
sudo python xls2cvs variants.xls > variants.csv
```

However, when I move it to the server (Ubuntu 10.04.2 LTS), it does not work. It complains....
```
ionadmin@ionT01:/results/analysis/output/Home/TuesdayJuly31_064/plugin_out/variantCaller_out/IonXpress_001$ python /home/ionadmin/tools/pyexcelerator-0.6.4.1/tools/xls2csv.py variants.xls > variants.csv
extracting data from variants.xls
Traceback (most recent call last):
  File "/home/ionadmin/tools/pyexcelerator-0.6.4.1/tools/xls2csv.py", line 17, in <module>
    for sheet_name, values in parse_xls(arg, 'cp1251'): # parse_xls(arg) -- default encoding
  File "/usr/local/lib/python2.6/dist-packages/pyExcelerator/ImportXLS.py", line 327, in parse_xls
    ole_streams = CompoundDoc.Reader(filename).STREAMS
  File "/usr/local/lib/python2.6/dist-packages/pyExcelerator/CompoundDoc.py", line 63, in __init__
    self.__build_header()
  File "/usr/local/lib/python2.6/dist-packages/pyExcelerator/CompoundDoc.py", line 105, in __build_header
    raise Exception, 'Not an OLE file.'
Exception: Not an OLE file.
```

I know Ubuntu has Python 2.6 installed and I made sure the module supports 2.6 and it does (2.4 and above).

This leads me to believe that there is a dependency missing. How can I find this dependency? It is essential to get the csv to make our pipeline-ing go a lot smoother. Thanks in advance!

---

### Post by ajgreeny on 2012-07-31
This does not actually answer your specific question, but you could open the xls file in your spreadsheet application (Libreoffice or gnumeric, etc etc) and simply save it as a .csv file.

Of course, I may have not followed your reasoning for needing to do it the way you want.

---

### Post by cheerPuncH on 2012-08-01
Right, I could do that, but our machine outputs 32xls files and I need them in csv form so I can run a script on them. It would be a pain in the butt to open open office for each file. I'm trying to automate everything. Is there a way to find out the differences between the dependencies on my local computer and my remote computer?
Thanks for your response!

---

### Post by cheerPuncH on 2012-09-04
I was never able to solve this. I just reformatted the data with scripting.

---

### Post by drmrgd on 2012-09-05
I have to ask, do you really need to convert the .xls file?  On our server, I believe it's a csv by default that they just had the software tag with an .xls extension.  Whenever I open those variants.xls files with Excel on my Windows box, it complains that it might not be an Excel file and asks if I really want to open it.  Also, if I just run 'more' on those files, it shows as a tab delimited file, and I think try Excel files show something else.  

So if you need it comma separated for sure, I'll bet a quick awk or sed statement would suffice:

```
sed 's/\t/\,/g' variants.xls > variants.csv
```

---


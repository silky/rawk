                                            _                   
               _      _ __  __ _ __      __| | __     _         
              (_)    | '__|/ _` |\ \ /\ / /| |/ /    (_)             
            _  _     | |  | (_| | \ V  V / |   <      _  _ 
           (_)(_)    |_|   \__,_|  \_/\_/  |_|\_\    (_)(_)
                                                                     


.:[ rage against web frameworks! ]:.

rawk: a markdown-based web framework using only unix commandline tools    
license: public domain and isc dual-license

design goals:
0. simplicity: very customisable but works nearly straight out of the box
0. posix-compliant tools: uses only strict posix compliant syntax for the 
unix command line tools it uses (i.e. sh and sed)
0. no gui required
0. lynx-friendly

installation
0. ./config.sh or PREFIX=${HOME} ./config.sh
0. make 
0. make sure a markdown parser is installed / available

quick notes:
* rawk looks for rawkrc in the current directory
* rawk expects at a minimum a path to a tree of markdown files
* rawk also looks for a second argument which is the output directory
* if no output directory rawk will use $PWD/$(basename $1).build
* by default rawk looks for smu; feel free to switch out your markdown parser.
smu can be obtained from its [homepage](http://s01.de/~tox/index.cgi/proj_smu)
or by clicking the link at the bottom right of the page.
* rawk identifies markdown files by the extension .md

quick start (the way i do it):

0. create a directory for your site, ex. brokenlcd.net

0. create a directory inside that to hold the actual site source, i.e. 
brokenlcd.  right now, my site directory looks like:

    `kyle@sterling [ ~/src ] $ ls`    
    `brokenlcd.net/`    
    `kyle@sterling [ ~/src ] $ ls brokenlcd.net/`    
    `brokenlcd/`   

0. copy the sample makefile, templates, and rawkrc from 
$PREFIX/share/rawk/site to your site directory, i.e.:

    `kyle@sterling [ ~/src ] $ ls brokenlcd.net/`   
    `brokenlcd/  templates/      Makefile    rawkrc`

0. edit rawkrc, changing SITE\_TITLE and SITE\_SUBTITLE to match your site. 
you want to use a different markdown interpreter, set MDPARSER 
appropriately. 

0. edit the Makefile to rename the SITE and rsync details (for uploading
the site).

0. make && make install

0. take a look at [the tutorial](tutorial.html) for a longer tutorial.

customisations
* the header template should / can contain the following vars:    
`${title}        # site title`    
`${subtitle}     # site subtitle`
`${root\_link}    # the site root (use in an href)`     
`${date}         # unix time stamp (i.e. $(date))`    

* you can point rawkrc at your own header / footer templates and stylesheet
in rawkrc    

* you can change the site root to use for links in the variable SITE\_ROOT    
the default is SITE\_ROOT="/" so the root links are `<a href="/index.html">`

* you are encouraged to tweak the source so it does precisely what you wish    

* setting the variable uname_comment to anything prints the interpreter,
`date`, and `uname -rms` to the body as a comment     

links
* $PREFIX/share/rawk/
* [ASCII art generator](http://www.network-science.de/ascii/)

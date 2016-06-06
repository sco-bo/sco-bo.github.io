---
layout: post
title:  "Using Jekyll and GitHub Pages to make your static site"
date:   2016-06-05
categories: jekyll
tags: [jekyll, github]
---

**Jekyll** is a static site generator, which has become the preferred tool of GitHub Pages. It has also become an ideal service for building a website for your friend's jewelry store in only a weekend. 

One of the many great features of Jekyll is that it sets up the framework for you to write clean and easy HTML and CSS. This format is ideal for websites that don't need a database, such as portfolio or personal websites. No database also means no need to worry about a hack or data breach. These sites just serve up old fashioned HTML. 

When data is needed, such as data that would ordinarily have been pulled from a database, Jekyll utilizes Liquid Tags and YAML data files to serve that content, looping through it, much like a 'for loop':

{% gist 7616a164e65aedb5cb826d16f0afce64 %}

In this blog entry we'll  go into setting up a personal site using Jekyll and using GitHub Pages as our [host](https://en.wikipedia.org/wiki/Web_hosting_service). 

I chose GitHub Pages as the host for my site, but there are many other great hosts out there. In my quest to build my site, [DigitalOcean](https://www.digitalocean.com/) and [Bluehost](https://www.bluehost.com/) were also both highly recommended for good entry-level small website hosting. However, these hosts seemed like overkill for what I needed. I simply wanted a place to show projects I'd built, my contact info, and my blog. I didn't necessarily need a host that would dynamically scale to handle millions of users being on my site at the same time (although who knows, maybe this blog entry will take off and crash my site). For that purpose, GitHub Pages fit the bill for the perfect host, and they host for free! 

For those of you who are already familiar with creating and using GitHub to store your code, this GitHub Pages setup will probably be a breeze. Even so, we'll walk through the process step by step. 

### Preface
This walk-thru assumes that [git](https://git-scm.com/) is on your local machine and that you are somewhat familiar with git. The walk-thru also assume you have a Ruby manager installed (either [rbenv](https://github.com/rbenv/rbenv) or [rvm](https://rvm.io/)) and that you have familiarity with the command line. 

### Step 1
Let's start by creating a new repository on GitHub. The name of this repository will be your username, followed by .github.io. In my case, sco-bo.github.io. Make sure the repository is Public, not Private and in this case, let's not check the box to initialize the repository with a README. Then, at the bottom of the page click 'Create repository'. Finally, click the little clipboard icon to copy the repository directory (using either HTTPS or SSH, I usually use SSH). Great! You have just made the first step toward creating the repository where your website files will be hosted. 

### Step 2
Open your terminal window. Navigate to the folder where you want to store your website folder and all of its content. Then, in your terminal type `mkdir` followed by your github repo name. In my case: 

    mkdir sco-bo.github.io

Now, `cd` into this folder and in your terminal type: 
	
    git init

then type `git remote add origin` and paste the link you copied from step 1. So in my case, it looks like this: 

    git remote add origin git@github.com:sco-bo/sco-bo.github.io

### Step 3
While in your project folder, type the following in your terminal: 

    touch Gemfile

This will create a Gemfile in your project's root folder. Open the file in your text editor and add the following to it: 

    source 'https://rubygems.org'
    gem 'github-pages', group: :jekyll_plugins
 
Then, go back to your terminal and run `bundle install`. This will install all the appropriate dependencies for setting up and maintaining Jekyll. According to the documentation of the github-pages gem: 

> The goal of the GitHub Pages gem is to help GitHub Pages users bootstrap and maintain a Jekyll build environment that most closely matches the GitHub pages build environment. The GitHub Pages gem relies on explicit requirements shared between both users' computers and the build servers to ensure that the result of a user's local build is consistently also the result of the server's build.

### Step 4
Now, in your terminal, type: 

    jekyll new . --force

This should create a bunch of folders and files. Congratulations! These are all the building blocks of your new site! To see what the pages look like, open a new terminal window and type: 

    jekyll serve --watch

This command starts running a development server, much like `rails server` does in rails projects. To view your site, navigate your browser to http://localhost:4000/. Congrats! This is your new jekyll site! Now, it probably looks much different from the way you want it to look (what you see is the filler text from Jekyll showing all the possibilities of things you can do) but you have already come a long way. Pat yourself on the back! 

### Step 5
We now need to add and commit the changes we've made and push them up to Github. Do this in your terminal by running 

    git add -A
    git commit -m "Initial jekyll commit"
    git push -u origin master 

It may take a few seconds, but now when you point your browser to **yourusername.github.io** (in my case sco-bo.github.io) you will see your new jekyll site there! Next comes the exciting part, making this site your own and styling it to be a true reflection of you! To learn more about some of the great features and general structure of Jekyll, consider checking out this video, which was quite helpful to me: 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qJQNJcm-edk" frameborder="0" allowfullscreen></iframe>
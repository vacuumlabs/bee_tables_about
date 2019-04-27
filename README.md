# Bee Tables

The mission of Bee Tables is to create a configurable and robust place for your business data.

Bee Tables is not another CRM or an accounting system. Bee Tables is mission-agnostic tool
resembling Excel or Google Sheets. The core features include powerful scripting language support
(Javascript), audibility of all changes, configurable approval process, and granular access rights.

This comes at a cost: We've sacrificed some [WYSIWYG](https://en.wikipedia.org/wiki/WYSIWYG)
features of Excel. This means that only engineer with at least basic knowledge of programming is able to
set up the project, create tables, calculate views, use external data sources and setup access-rights
logic. Once the project structure is ready, users can manipulate data just like with Excel, but
without constant fear, they'll break something.

## Sample use-case for Bee Tables

The company wants to create an internal accounting system for managing their suppliers. While many
solutions exist for such a task, let us show, what you can achieve with Bee Tables. Product owners
have the following requirements on the system:

- The finance department can create and edit ledger entries for individual suppliers. Finance department
  cannot edit ledger entries older than 1 month without approval of the management.
- If turnover on a ledger of a certain supplier ledger exceeds $10k per month, the management is
  notified via e-mail.
- Office department cannot see the majority of the suppliers' data, but they can see (not edit)
  suppliers that are labeled as 'office'.
- Simple machine learning model is used to predict, how much the company is going to spend to the individual
  suppliers. The ML is here to discover trends (in Winter we usually pay more money to X).
- Individual suppliers can log in to the system and see their individual ledgers.
- Calendar view shows due-dates for delivering goods and paying invoices.
- The system can use the current conversion rate to convert between various currencies.

While multiple table processors can do some parts of such feature set, no-one can do everything (not
even close to it!). With Bee Tables, one week of engineering work is enough to configure such a
system!

## Feature set

### Authentication

Users can sign in via Google, Facebook, Github, LinkedIn or use username + password.

### History

Unlike Google Sheets, new changes are grouped to _patches_. You can review what changes were made
with individual patches, or you can easily see who changed the given value, when and what other changes were
part of this patch. You can recover the document to any given point in history.

### Approval process for new changes

It's common practice in the software development world that changes are reviewed first by their author
then by peers and only then they are applied to the codebase. This practice is so widespread, that
[many](https://github.com/) [ecosystems](https://bitbucket.org/product/) were created to allow
programmers to use such workflows. We believe that adopting similar practices for working with data is
necessary to maintain high quality of your dataset.

Before the user produces a patch of changes, they are prompted to review what exactly they have changed. This
is a perfect way to filter out some mistakes such as accidentally changed field or half-finished-change.
Once the patch is reviewed by its author, it may be subjected to further review.

The review process is configurable, so you can define your own business rules for how many approvals
and from what roles are needed for a patch to be applied to the dataset. For example, changing the user's
address can be done by HR, but changing the user's salary needs at least one confirmation from
management.

### Custom views

By default, data is displayed in the form of the table. The system can, however, support custom views
(requires coding). Data you have can be visualized as the chart, calendar, Kanban board or plan of the building.

The views are implemented using HTML + CSS. There is a good reason for this: In Excel, all you can do
to achieve a nice look of your table is to customize colors, borders, fonts and (if you're pro)
marge cells. This is a nice start, but this is no way how to create top-tier visualizations. On the
other hand, HTML + CSS is used by millions of projects to achieve exactly this.

### Powerful scripting language

The scripting language is Javascript. This means, that the vast majority of system configuration needs
to be done by engineers (either internal resource, or can be supplied by Vacuumlabs). Using
Javascript as scripting language gives engineers a lot of power: They can do complex calculations at
ease, use tons of existing chart libraries, create beautiful visuals, and even train Machine
Learning models on top of your data!

### Granular access rights

As with Sheets, you can grant read/write permissions to individual datasets. The permission model, however, is much more granular than just this. You can allow a user to see some selection of the data,
or allow them to do only certain changes. For example, you can let you HR approve small expenses. If
they mistakenly try to approve higher value, the permission system kicks in!

### Legislation loves custom hosting

The system can be deployed on-premise to your existing infrastructure. This means, that even in
unlike event of hacking the system, data are in perfect isolation from other companies' data.
Moreover, this allows you to store data in geographic location and with such encryption, that is
compliant with your regulation.

## Limitations

- 100 million of cells per table
- No native mobile client at the moment (possible to use a web browser)
- At the moment, the system recognizes only tabular views. Other views need to be implemented for
  the specific use-case.

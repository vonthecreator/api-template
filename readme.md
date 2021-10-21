# API-TEMPLATE
<br/>
<br/>
## How it all works
<br/>
<br/>


Essentially, the variable `query` gets populated with however many filters we want to user on our database. This is even better than rerouting every single column in the database onto a different url like in traditional static APIs. 
<br/>
<br/>
<br/>


#### It's all about `query`
In the `/api/v1/resources/books?column_filter` we notice that inside the api_filter(), the variable `query` is declared as a string. However, right below follows a series of boolean expresssions that make our filtering possible...
<br/>

Within these booleans, all the operations inside are pretty much the same. Our variable query gets populated by an additional string each step of the way; in the first place being we have: `query += ' id=? AND'`. 
<br/>

#### cur.execute()
But finally at the end of the logical expressions; our results are assigned to cur.execute(), which holds our query and column_filters. Basically meaning when our JSON gets displayed, to_filter.fetchall is going to show us a display of all the filters inside our query statement. 
<br/>

In other words: just because you have the query, it don't mean I will show you the results. That means, even if the SQL database finds our results, it's still our repsonsibliity as the developer to fetchall() using a filter. 

<br/>

#### dict_factory()
dict_factory iterates our database while keeping track of our index and Object. Finaly, the result is a an Object that then prepares us to turn the data into JSON format. 



What would be really cool to see is how to write to our database coming from JSON format into our SQLITE database.
Consider the fundamental model in network analysis, which at the population level can be described as:  

$$
P(D_{k+1} = 1 \mid D_k, Z) = \frac{\exp(\alpha + \beta_1 D_k + \beta_2 Z)}{1 + \exp(\alpha + \beta_1 D_k + \beta_2 Z)}
$$

Here, $D_{k+1}$ represents some disease (e.g., a phecode), and we are studying the effect of $D_k$ on $D_{k+1}$ for every possible pair from $k$ to $K$. $Z$ is a vector of PCA-derived covariates used to account for other diseases.  

Considering this model, we want to deconfound the $D_{k+1} \sim D_k$ association from all family-level confounders (i.e., we seek the estimand $P(D_{k+1} &#124; do(D_k))$ ). Such confounders could produce networks that are non-causal but instead reflect shared family factors (e.g., genetics, household socioeconomic conditions, parental healthcare-seeking patterns).  

From the marginal between–within model, we know that any exposure ($D_k$) can be adjusted for family-level confounding by including the average exposure $\bar{D}_k$ across each sibling pair. Typically, both siblings are retained in the model, but in our case only the “cases” are included. However, we can still include $\bar{D}_k$ using the known $D_k$ status of the sibling, without needing the sibling directly in the model. This yields:  

$$
P(D_{k+1} = 1 \mid D_k, Z, \bar{D}_k) = \frac{\exp(\alpha + \beta_1 D_k + \beta_2 Z + \beta_3 \bar{D}_k)}{1 + \exp(\alpha + \beta_1 D_k + \beta_2 Z + \beta_3 \bar{D}_k)}
$$

Note that family-level confounding may also affect the covariate vector $Z$. To address this fully, we additionally include the sibling-pair mean of $Z$, denoted $\bar{Z}$, giving:  

$$
P(D_{k+1} = 1 \mid D_k, Z, \bar{D}_k, \bar{Z}) = \frac{\exp(\alpha + \beta_1 D_k + \beta_2 Z + \beta_3 \bar{D}_k + \beta_4 \bar{Z})}{1 + \exp(\alpha + \beta_1 D_k + \beta_2 Z + \beta_3 \bar{D}_k + \beta_4 \bar{Z})}
$$
